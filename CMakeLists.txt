cmake_minimum_required (VERSION 2.6)
project (MoDesA)

# set module path to custom cmake modules
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/modules")

# topmodule is allways required
include(topmodule)

# some general settings
set(CMAKE_C_COMPILER gcc)
set(CMAKE_CXX_COMPILER g++)

#############################
# MoDesA specific settings
#############################

# set matlab on for matlab code generation
set(matlab "on")
#set synthesis on for synthesis
set(synthesis "on")

#
# declare name and path within of Simulink model
# model need to be in models folder
#

set(model_name "test_model_hw_only")
#set(model_name "test_model_hw_sw")
#set(model_name "test_model_hw_sw_hw_sw")
#set(model_name "test_model_sw_hw")
#set(model_name "test_model_sw_only")

set(model_path "test_model")


# default option to profile sw execution of the model
set(profiling "off")
# default device = ZedBoard
#set(device "xc7z020clg484-1")
# ZCU106
set(device "xczu7ev-ffvc1156-2-e")
# set board name only for pure HW, ex "ZCU106" or OFF otherwise
set(board "OFF")
# default clk = 10 ns = 100MHz
set(clk "10")
# set accurate for synthesis evaluation with Vivado
# default fast just VivadoHLS synthesis
set(syn_opt "fast")

# here we call the topmodule with all the parameters
topmodule(${synthesis} ${matlab} ${profiling} ${model_name} ${model_path} ${device} ${board} ${clk} ${syn_opt})

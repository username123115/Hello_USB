# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialise pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH "/Users/danieljin/Desktop/Pico/pico-sdk")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(USB_Hello_World C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()


#some tests
#-----
if (TARGET tinyusb_device)
    message("Is Tinyusb device")
endif ()
if (TARGET tinyusb_host)
    message("Is Tinyusb host")
endif ()
#-----


# Add executable. Default name is the project name, version 0.1

add_executable(USB_Hello_World)
target_sources(USB_Hello_World PUBLIC 
                ${CMAKE_CURRENT_LIST_DIR}/main.c)

# Make sure TinyUSB can find tusb_config.h
target_include_directories(USB_Hello_World PUBLIC
        ${CMAKE_CURRENT_LIST_DIR})

pico_set_program_name(USB_Hello_World "USB_Hello_World")
pico_set_program_version(USB_Hello_World "0.1")

pico_enable_stdio_uart(USB_Hello_World 1)
pico_enable_stdio_usb(USB_Hello_World 1)

# Add the standard library to the build
# target_link_libraries(USB_Hello_World pico_stdlib tinyusb_device, tinyusb_board)
target_link_libraries(USB_Hello_World pico_stdlib)

pico_add_extra_outputs(USB_Hello_World)


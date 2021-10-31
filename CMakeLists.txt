cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)
project(target C CXX ASM)

SET(CMAKE_C_STANDARD 11)
SET(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

include_directories(
  src
  ${CMAKE_SOURCE_DIR}
)

set(target_SRC
  src/main.S
)

add_executable(target ${target_SRC})

pico_enable_stdio_usb(target 1)

# Create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(target)

target_link_libraries(target pico_stdlib)

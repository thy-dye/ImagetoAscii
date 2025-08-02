cmake_minimum_required(VERSION 4.0.3)
project(IMAGETOASCII)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(SDL_LIB "${CMAKE_SOURCE_DIR}/libs/SDL/libSDL3-debug.a")
set(SDL_INCLUDE "${CMAKE_SOURCE_DIR}/libs/SDL/include")

add_executable(${PROJECT_NAME} WIN32
    src/main.cpp
)

target_compile_options(${PROJECT_NAME} PRIVATE
    -g
    -Wall
    -pedantic-errors
    -Werror
    -std=c++23
)

target_include_directories(${PROJECT_NAME} PRIVATE 
    ${SDL_INCLUDE}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    ${SDL_LIB}
    mingw32  # Required for MinGW entry point
    opengl32 # For OpenGL support (if used)
    imm32    # Input Method Manager (for IME)
    winmm    # Windows Multimedia (timer/sound)
    version  # Version API
    setupapi # Device installation
    advapi32 # Advanced API services
    shell32  # Shell API
    user32   # User interface
    gdi32    # Graphics Device Interface
    ole32    # OLE (Object Linking and Embedding)
    oleaut32 # OLE Automation
)
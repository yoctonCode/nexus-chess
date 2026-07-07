# CMakeList.txt : CMake project for NexusChess, include source and define
# project specific logic here.
#

# Add source to this project's executable.
add_executable (NexusChess "NexusChess.cpp" "NexusChess.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET NexusChess PROPERTY CXX_STANDARD 20)
endif()

target_sources(NexusChess PRIVATE
  ../vendor/imgui/imgui.cpp
  ../vendor/imgui/imgui_draw.cpp
  ../vendor/imgui/imgui_demo.cpp
  ../vendor/imgui/imgui_tables.cpp
  ../vendor/imgui/imgui_widgets.cpp
  ../vendor/imgui/backends/imgui_impl_sdl3.cpp
  ../vendor/imgui/backends/imgui_impl_opengl3.cpp
)
target_include_directories(NexusChess PRIVATE
  ../vendor/imgui
  ../vendor/imgui/backends
)
find_package(SDL3 CONFIG REQUIRED)
target_link_libraries(NexusChess PRIVATE SDL3::SDL3 opengl32)

# TODO: Add tests and install targets if needed.

# SPDX-License-Identifier: BSD-3-Clause
# Copyright Contributors to the OpenEXR Project.

add_executable(exrmaketiled 
  makeTiled.cpp
  main.cpp
  Image.cpp
)
target_link_libraries(exrmaketiled OpenEXR::OpenEXR)
set_target_properties(exrmaketiled PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)
install(TARGETS exrmaketiled DESTINATION ${CMAKE_INSTALL_BINDIR})
if(WIN32 AND (BUILD_SHARED_LIBS OR OPENEXR_BUILD_BOTH_STATIC_SHARED))
  target_compile_definitions(exrmaketiled PRIVATE OPENEXR_DLL)
endif()

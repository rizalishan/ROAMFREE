ADD_LIBRARY(solver_cholmod SHARED
  solver_cholmod.cpp
  linear_solver_cholmod.h
)

INCLUDE_DIRECTORIES(${CHOLMOD_INCLUDE_DIR})

SET_TARGET_PROPERTIES(solver_cholmod PROPERTIES OUTPUT_NAME ${LIB_PREFIX}solver_cholmod)

TARGET_LINK_LIBRARIES(solver_cholmod ${CHOLMOD_LIBRARIES} ${BLAS_LIBRARIES} core)

INSTALL(TARGETS solver_cholmod
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
  LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
  ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)

FILE(GLOB headers "${CMAKE_CURRENT_SOURCE_DIR}/*.h" "${CMAKE_CURRENT_SOURCE_DIR}/*.hpp")

INSTALL(FILES ${headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/g2o/solvers/cholmod)

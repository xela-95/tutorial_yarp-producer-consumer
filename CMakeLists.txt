# requires minimum cmake version
cmake_minimum_required(VERSION 2.8.9)

# produce the cmake var PROJECT_NAME
project(tutorial_producer-consumer)

# mandatory use of these packages
find_package(YARP 3.0 REQUIRED)

find_package(ICUBcontrib REQUIRED)

# extend the current search path used by cmake to load helpers
list(APPEND CMAKE_MODULE_PATH ${ICUBCONTRIB_MODULE_PATH})

include(ICUBcontribHelpers)
# specify to install in $ICUBcontrib_DIR/bin
icubcontrib_set_default_prefix()

############## Ports
add_executable(tutorial_yarp-producer-port ${CMAKE_SOURCE_DIR}/port/producer.cpp)
target_link_libraries(tutorial_yarp-producer-port ${YARP_LIBRARIES})

install(TARGETS tutorial_yarp-producer-port DESTINATION bin)

add_executable(tutorial_yarp-consumer-port ${CMAKE_SOURCE_DIR}/port/consumer.cpp)
target_link_libraries(tutorial_yarp-consumer-port ${YARP_LIBRARIES})

install(TARGETS tutorial_yarp-consumer-port DESTINATION bin)

############## BufferedPorts
add_executable(tutorial_yarp-producer-buff ${CMAKE_SOURCE_DIR}/bufferedport/producer.cpp)
target_link_libraries(tutorial_yarp-producer-buff ${YARP_LIBRARIES})

install(TARGETS tutorial_yarp-producer-buff DESTINATION bin)

add_executable(tutorial_yarp-consumer-buff ${CMAKE_SOURCE_DIR}/bufferedport/consumer.cpp)
target_link_libraries(tutorial_yarp-consumer-buff ${YARP_LIBRARIES})

install(TARGETS tutorial_yarp-consumer-buff DESTINATION bin)
icubcontrib_add_uninstall_target()

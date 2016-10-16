cmake_minimum_required(VERSION 2.8.3)
project(ca_driver)

find_package(libcreate REQUIRED)
find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  geometry_msgs
  nav_msgs
  sensor_msgs
  tf
  ca_msgs
  diagnostic_msgs
  diagnostic_updater
)

find_package(Boost REQUIRED system thread)

catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS roscpp std_msgs geometry_msgs nav_msgs sensor_msgs tf ca_msgs ca_description diagnostic_msgs diagnostic_updater
  DEPENDS libcreate
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(ca_driver src/create_driver.cpp)

target_link_libraries(ca_driver
  ${catkin_LIBRARIES}
  libcreate::create
)

---
title: "librt linking error during rospackage compile"
date: 2012-11-01
forum: Programming Talk
---

### Post by mdemirst on 2012-11-01
I am getting this error below during compilation:

```
  [100%] Building CXX object CMakeFiles/vn_100_pub.dir/src/publisher/vn_100_publisher.o
  /home/mahmutdemir/ros_stacks/vn_100/src/publisher/vn_100_publisher.cpp: In function ‘int main(int, char**)’:
  /home/mahmutdemir/ros_stacks/vn_100/src/publisher/vn_100_publisher.cpp:17:11: warning: unused variable ‘ypr’ [-Wunused-variable]
  Linking CXX executable ../bin/vn_100_pub
  /usr/bin/ld: ../lib/liblvn_100.a(vncp_services.o): undefined reference to symbol 'clock_gettime@@GLIBC_2.2'
  /usr/bin/ld: note: 'clock_gettime@@GLIBC_2.2' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/librt.so so try adding it to the linker command line
  /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/librt.so: could not read symbols: Invalid operation
  collect2: ld returned 1 exit status
```

I think it is related to some linker errors. Here is my cmakefile:

```
cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)

set(ROS_BUILD_STATIC_LIBS true)
set(ROS_BUILD_SHARED_LIBS false)

rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#uncomment if you have defined messages
#rosbuild_genmsg()
#uncomment if you have defined services
#rosbuild_gensrv()

set (CMAKE_CXX_FLAGS "-Iinclude/" )
rosbuild_add_library(lvn_100 src/publisher/vn_100_publisher.cpp)
rosbuild_add_library(lvn_100 src/vn100.c)
rosbuild_add_library(lvn_100 src/arch/linux/vncp_services.c)

set (CMAKE_CXX_FLAGS "-pthread -lrt" )
set (CMAKE_LD_FLAGS "-pthread -lrt" )
rosbuild_add_executable(vn_100_pub src/publisher/vn_100_publisher.cpp)
target_link_libraries(vn_100_pub lvn_100)

```

I have searched through web but most of the problems were solved by adding -lrt to the linker line. I am not sure where to add -lrt or not sure even this error is related to some linker error.

Any suggestion will be greatly appreciated..

---

### Post by spjackson on 2012-11-01
I don't know cmake. However, I suspect that this is wrong
```

set (CMAKE_CXX_FLAGS "-pthread -lrt" )
set (CMAKE_LD_FLAGS "-pthread -lrt" )

```
I think this will result in the libraries appearing before the objects in the link command. The libraries need to be after the objects.

As I say, I don't know cmake, but perhaps you need to use TARGET_LINK_LIBRARIES.

---


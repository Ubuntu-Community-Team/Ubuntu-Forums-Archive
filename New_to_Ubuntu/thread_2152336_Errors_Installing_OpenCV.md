---
title: "Errors Installing OpenCV"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by Lieske on 2013-06-07
I'm currently trying to install open cv using [this guide]("http://www.raben.com/content/opencv-installation-ubuntu-1204").

When I run:

```

cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local
-D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON
-D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON
-D BUILD_EXAMPLES=ON -D WITH_QT=ON -D WITH_OPENGL=ON .. 
```

I get the following error:
```

CMake Warning at cmake/OpenCVFindLibsGUI.cmake:22 (find_package):
  Could not find module FindQt5Test.cmake or a configuration file for package
  Qt5Test.

  Adjust CMAKE_MODULE_PATH to find FindQt5Test.cmake or set Qt5Test_DIR to
  the directory containing a CMake configuration file for Qt5Test.  The file
  will have one of the following names:

    Qt5TestConfig.cmake
    qt5test-config.cmake

Call Stack (most recent call first):
  CMakeLists.txt:381 (include)


CMake Warning at cmake/OpenCVFindLibsGUI.cmake:23 (find_package):
  Could not find module FindQt5Concurrent.cmake or a configuration file for
  package Qt5Concurrent.

  Adjust CMAKE_MODULE_PATH to find FindQt5Concurrent.cmake or set
  Qt5Concurrent_DIR to the directory containing a CMake configuration file
  for Qt5Concurrent.  The file will have one of the following names:

    Qt5ConcurrentConfig.cmake
    qt5concurrent-config.cmake

Call Stack (most recent call first):
  CMakeLists.txt:381 (include)


-- Looking for linux/videodev.h
-- Looking for linux/videodev.h - not found
-- Looking for linux/videodev2.h
-- Looking for linux/videodev2.h - found
-- Looking for sys/videoio.h
-- Looking for sys/videoio.h - not found
-- Looking for libavformat/avformat.h
-- Looking for libavformat/avformat.h - found
-- Looking for ffmpeg/avformat.h
-- Looking for ffmpeg/avformat.h - not found
-- Could NOT find OPENCL (missing:  OPENCL_LIBRARY OPENCL_INCLUDE_DIR) 
 
```

This does produce build files but I'm assuming the build files are broken because when I try to run 'make' the following error happens:

```
[ 12%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/window_QT.cpp.o
In file included from /home/.../OpenCV/opencv/modules/highgui/src/window_QT.cpp:46:0:
/home/.../OpenCV/opencv/modules/highgui/src/window_QT.h:81:17: fatal error: QTest: No such file or directory
compilation terminated.
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/window_QT.cpp.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2

```.


Does anyone know what is happening?

---

### Post by obiwang on 2013-07-11
ALL CMake file you need are under the path 

...../Qt5.1.0/5.1.0/gcc/lib/cmake

not in the .../Qt5.1.0/5.1.0/gcc/lib/

I specified them under cmake-gui one by one ( Qt5Core_DIR , Qt5Test_DIR .....)

If there is any EGL or OpenGL error shows up

You have to install OpenGL 


sudo apt-get install build-essential
sudo apt-get install libgl1-mesa-dev

---


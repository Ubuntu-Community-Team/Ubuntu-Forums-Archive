---
title: "i need help with installing opencv"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by chiara3 on 2014-03-19
Hi I'm trying to install openCV, 
I'm follow this instruction:
 
[http://miloq.blogspot.it/2012/12/install-opencv-ubuntu-linux.html](http://miloq.blogspot.it/2012/12/install-opencv-ubuntu-linux.html)

 but before passage 5 i have this message

CMake Warning at cmake/OpenCVFindLibsGUI.cmake:22 (find_package):
  By not providing "FindQt5Concurrent.cmake" in CMAKE_MODULE_PATH this
  project has asked CMake to find a package configuration file provided by
  "Qt5Concurrent", but CMake did not find one.

  Could not find a package configuration file provided by "Qt5Concurrent"
  with any of the following names:

    Qt5ConcurrentConfig.cmake
    qt5concurrent-config.cmake

  Add the installation prefix of "Qt5Concurrent" to CMAKE_PREFIX_PATH or set
  "Qt5Concurrent_DIR" to a directory containing one of the above files.  If
  "Qt5Concurrent" provides a separate development package or SDK, be sure it
  has been installed.
Call Stack (most recent call first):
  CMakeLists.txt:434 (include)


qmake: could not find a Qt installation of ''
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:1382 (message):
  Found unsuitable Qt version "" from NOTFOUND, this code requires Qt 4.x
Call Stack (most recent call first):
  cmake/OpenCVFindLibsGUI.cmake:34 (find_package)
  CMakeLists.txt:434 (include)


What can I do?

Thanks

---

### Post by steeldriver on 2014-03-19
Hello and welcome to the forums

What version of Ubuntu are you running? What version of OpenCV are you trying to install?

If you don't need a more recent version, then by far the easiest option is to install the binary package supplied by your distribution (i.e. just install the libopencv-dev package)

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
I had quite a bit of trouble with this too, I was trying to install 2.4.3.  It turned out that 2.4.3 didn't support QT5.  I had to use 2.4.6 (or higher).

-DM

---


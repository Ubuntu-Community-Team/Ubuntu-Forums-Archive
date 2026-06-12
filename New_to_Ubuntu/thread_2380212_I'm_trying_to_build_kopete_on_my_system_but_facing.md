---
title: "I'm trying to build kopete on my system but facing an error while cmake."
date: 2017-12-14
forum: New to Ubuntu
---

### Post by mahesh6947 on 2017-12-14
[FONT=monospace][COLOR=#000000]PATH= ..       [/COLOR]
-- Found Qt-Version 5.7.1 (using /usr/bin/qmake)
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
QT_QT_INCLUDE_DIR
   used as include directory in directory /home/mahesh/devel/src/kopete/build/CMakeFiles/CMakeTmp

CMake Error: Internal CMake error, TryCompile configure of cmake failed

CMake Error at /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake:1283 (message):
  Unable to compile a basic Qt application.  Qt has not been found correctly.
Call Stack (most recent call first):
  //share/cmake-3.0/Modules/FindKDE4.cmake:108 (find_package)
  CMakeLists.txt:4 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/mahesh/devel/src/kopete/build/CMakeFiles/CMakeOutput.log".
See also "/home/mahesh/devel/src/kopete/build/CMakeFiles/CMakeError.log".

[/FONT]

---

### Post by mastablasta on 2017-12-15
any special reason you are building it yourself? is it not in repository?

there is also a PPA: [https://launchpad.net/~pali/+archive/ubuntu/kopete](https://launchpad.net/~pali/+archive/ubuntu/kopete)

---

### Post by leunam12 on 2017-12-15
Before building a program from source it is strongly advised that you make a backup of your whole system unless you know very well what you are doing. It is very easy to render your system unusable.

---


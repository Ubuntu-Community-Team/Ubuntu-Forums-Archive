---
title: "CMake, and Qt env variable issue"
date: 2019-04-22
forum: Packaging and Compiling Programs
---

### Post by jpitz312 on 2019-04-22
Hello all,  I am trying to setup a rust mapping generator to Qt.  here is the link of article:

[https://www.vandenoever.info/blog/2017/09/10/time_for_rust_and_qml.html](https://www.vandenoever.info/blog/2017/09/10/time_for_rust_and_qml.html)

below is my .profile settings and the error I am getting:

I removed the original Qt5-default package I installed and performed a wget instead as the cmake files were missing for qt

When I now cmakeit appears cmake is looking ih the original location for qt cmake files.  I have removed and re-installed cmake.

The apt remove did not cleanly remove the Qt5 folders and cmake was looking for these instead of the new location.

I have tried to add various cmake env variables but still having issues.

Thanks 

Joe

CMake Error at CMakeLists.txt:50 (find_package):
  Could not find a package configuration file provided by "Qt5" (requested
  version 5.10.0) with any of the following names:

    Qt5Config.cmake
    qt5-config.cmake

  Add the installation prefix of "Qt5" to CMAKE_PREFIX_PATH or set "Qt5_DIR"
  to a directory containing one of the above files.  If "Qt5" provides a
  separate development package or SDK, be sure it has been installed.


export CMAKE_MODULE_PATH=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake
export CMAKE_SOURCE_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake
export CMAKE_PREFIX_PATH=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake
export ECM_DIR=/usr/share/ECM/cmake
export Qt5Core_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Core
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Config.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Qml.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Gui.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Quick.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5QuickControls2.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Widgets.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Test.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5QuickTest.cmake
# export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Svg.cmake
export CMAKE_MODULE_PATH=$CMAKE_MODULE_PATH:FindQt5Config.cmake

export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Qml
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Gui
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Quick
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5QuickControls2
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Widgets
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Test
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5QuickTest
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:Qt5Svg

export Qt5_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5
export Qt5Qml_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Qml
export Qt5Gui_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Gui
export Qt5Quick_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Quick
export Qt5QuickControls2_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5QuickControls2
export Qt5Widgets_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Widgets
export Qt5Test_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Test
export Qt5QuickTest_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5QuickTest
export Qt5Svg_DIR=/Home/Qt5.10.0/5.10.0/gcc_64/lib/cmake/Qt5Svg

---


---
title: "CMake Error and OIS library"
date: 2014-10-22
forum: Packaging and Compiling Programs
---

### Post by thibaud-ecarot on 2014-10-22
[B][COLOR=#333333]Hello everyone,

I try to write a CmakeList.txt with OIS library but it does not work.[/COLOR]
[COLOR=#333333]I write :[/COLOR]
```
find_package(OIS REQUIRED)
```[COLOR=#333333]
Error :[/COLOR]
    > CMake Error at CMakeLists.txt:21 (find_package):
  By not providing "FindOIS.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "OIS", but
  CMake did not find one.

  Could not find a package configuration file provided by "OIS" with any of
  the following names:

    OISConfig.cmake
    ois-config.cmake

  Add the installation prefix of "OIS" to CMAKE_PREFIX_PATH or set "OIS_DIR"
  to a directory containing one of the above files.  If "OIS" provides a
  separate development package or SDK, be sure it has been installed.

-- Configuring incomplete, errors occurred!
[COLOR=#333333]So i am blocked because i have installed these package : libois-1.3.0 libois-dev[/COLOR]
[COLOR=#333333]I have Ubuntu 14.04 with Xfce : Xubuntu.[/COLOR]
[COLOR=#333333]Can you help me ?[/COLOR]
[COLOR=#333333]Thanks in advance[/COLOR]
[/B]

---


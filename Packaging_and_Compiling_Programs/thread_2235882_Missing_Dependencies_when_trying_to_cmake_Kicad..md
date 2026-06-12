---
title: "Missing Dependencies when trying to cmake Kicad."
date: 2014-07-23
forum: Packaging and Compiling Programs
---

### Post by benjamin24 on 2014-07-23
Hi all!

I am trying to build Kicad PCB software on my linux distro (ubuntu server 14.04 with lubuntu-desktop, running as a virtual machine on OSX)

I am using [THIS]("http://www.kicad-pcb.org/display/DEV/Building+KiCad+on+Linux") tutorial and have already found a few missing dependancies that were not in the tutorial, however it seems I need some more? When I try and cmake I get the following message:

[I]benji@sputnik:~/build/kicad/kicad.bzr/build$ cmake -DKICAD_STABLE_VERSION=ON ../
-- Check for installed OpenGL -- found-- Found Glew: /usr/lib/x86_64-linux-gnu/libGLEW.so
-- Check for installed GLEW -- found
-- Could NOT find PkgConfig (missing:  PKG_CONFIG_EXECUTABLE) 
-- Could NOT find CAIRO, try to set the path to CAIRO root folder in the system variable CAIRO (missing:  CAIRO_LIBRARIES CAIRO_INCLUDE_DIR) 
-- Check for installed Cairo -- not found
CMake Error at CMakeModules/CheckFindPackageResult.cmake:6 (message):
  Cairo was not found - it is required to build Kicad
Call Stack (most recent call first):
  CMakeLists.txt:473 (check_find_package_result)

-- Configuring incomplete, errors occurred!
See also "/home/benji/build/kicad/kicad.bzr/build/CMakeFiles/CMakeOutput.log".[/I]

Any help is much appreciated.

Thanks!

---

### Post by oldos2er on 2014-07-23
Moved to Packaging & Compiling Programs.

---


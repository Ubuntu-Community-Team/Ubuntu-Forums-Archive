---
title: "problem in installation...Could NOT find CLHEP:"
date: 2015-10-07
forum: New to Ubuntu
---

### Post by ainnie on 2015-10-07
i am a new user of ubuntu. i am trying to install a simulation software Geant4. but i am stuck on one point. please help me n solving the error which i am facing. 

[EMAIL="ainnie@Nasr5"]ainnie@Nasr5[/EMAIL]:~/geant4$ cd geant4.10.01.p02-build
[EMAIL="ainnie@Nasr5"]ainnie@Nasr5[/EMAIL]:~/geant4/geant4.10.01.p02-build$ cmake -DCMAKE_INSTALL_PREFIX=~/geant4/geant4.10.01.p02-install -DGEANT4_USE_GDML=ON -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_RAYTRACER_X11=ON -DGEANT4_USE_SYSTEM_CLHEP=ON -DCLHEP_INCLUDE_DIR=/u/ey/perl/CLHEP/inc*lude/ -DCLHEP_LIBRARY=/u/ey/perl/CLHEP/lib/lib*CLHEP.so -DGEANT4_INSTALL_EXAMPLES=ON ~/geant4/geant4.10.01.p02
-- The C compiler identification is GNU 4.8.4
-- The CXX compiler identification is GNU 4.8.4
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at cmake/Modules/FindCLHEP.cmake:207 (file):
  file Internal CMake error when trying to open file:
  /u/ey/perl/CLHEP/inc*lude/CLHEP/Units/defs.h for reading.
Call Stack (most recent call first):
  cmake/Modules/Geant4OptionalComponents.cmake:58 (find_package)
  CMakeLists.txt:99 (include)    
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:108 (message):
  Could NOT find CLHEP:    
  Incompatible versions, (found) < 2.1.2.3(required)    
   (missing:  CLHEP_VERSION_COMPATIBLE) (Required is at least version "2.1.2.3")
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:315 (_FPHSA_FAILURE_MESSAGE)
  cmake/Modules/FindCLHEP.cmake:297 (find_package_handle_standard_args)
  cmake/Modules/Geant4OptionalComponents.cmake:58 (find_package)
  CMakeLists.txt:99 (include)   -- Configuring incomplete, errors occurred! See also "/home/ainnie/geant4/geant4.10.01.p02-build/CMakeFiles/CMakeOutput.log"

---

### Post by steeldriver on 2015-10-07
Hello and welcome to the forums

Check your command line for typos - in particular

```

-DCLHEP_INCLUDE_DIR=/u/ey/perl/CLHEP/**inc[COLOR=#ff0000]*[/COLOR]lude**/

```

isn't a valid directory name - resulting in the error

```

CMake Error at cmake/Modules/FindCLHEP.cmake:207 (file):
  file Internal CMake error when trying to open file:
  /u/ey/perl/CLHEP/**inc[COLOR=#ff0000]*[/COLOR]lude**/CLHEP/Units/defs.h for reading.

```

---


---
title: "Blender Compile fails Ubuntu 14.04"
date: 2014-04-24
forum: Packaging and Compiling Programs
---

### Post by GregPayne on 2014-04-24
Since i updated to Ubuntu 14.04 i can no longer compile blender. 

The problem seams to be related to the python version.  Python is reporting its version as 2.7. However as well as 2.7, 3.4 is also installed. Having done some research the compile error comes about when trying to use a version of python below 3.3. So my question is how do i make it use the correct python version? This compiled perfectly on 13.10 before i did the upgrade to 14.04. 

Hope someone can help :)


Terminal Output from the failed compile
=========================
Configuring Blender ...
# if test ! -f /home/gregpayne/sc/Blender cycles/build_linux/CMakeCache.txt ; then \
        #       cmake  -H"/home/gregpayne/sc/Blender cycles/blender-git-bake-cycles" -B"/home/gregpayne/sc/Blender cycles/build_linux" -DCMAKE_BUILD_TYPE:STRING=Release; \
        # fi
# do this always incase of failed initial build, could be smarter here...
cmake  -H"/home/gregpayne/sc/Blender cycles/blender-git-bake-cycles" -B"/home/gregpayne/sc/Blender cycles/build_linux" -DCMAKE_BUILD_TYPE:STRING=Release
-- The C compiler identification is GNU 4.8.2
-- The CXX compiler identification is GNU 4.8.2
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Performing Test SUPPORT_SSE_BUILD
-- Performing Test SUPPORT_SSE_BUILD - Success
-- SSE Support: detected.
-- Performing Test SUPPORT_SSE2_BUILD
-- Performing Test SUPPORT_SSE2_BUILD - Success
-- SSE2 Support: detected.
-- Performing Test HAVE_STDBOOL_H
-- Performing Test HAVE_STDBOOL_H - Success
CMake Warning at CMakeLists.txt:511 (message):
  Translation path '/home/gregpayne/sc/Blender
  cycles/blender-git-bake-cycles/release/datafiles/locale' is missing, This
  is a 'git submodule', which are known not to work with bridges to other
  version control systems, disabling 'WITH_INTERNATIONAL'.




CMake Warning at CMakeLists.txt:520 (message):
  Addons path '/home/gregpayne/sc/Blender
  cycles/blender-git-bake-cycles/release/scripts/addons' is missing, This is
  a 'git submodule', which are known not to work with bridges to other
  version control systems: * CONTINUING WITHOUT ADDONS *




-- Found JPEG: /usr/lib/x86_64-linux-gnu/libjpeg.so  
-- Found ZLIB: /usr/lib/x86_64-linux-gnu/libz.so (found version "1.2.8") 
-- Found PNG: /usr/lib/x86_64-linux-gnu/libpng.so (found version "1.2.50") 
-- checking for module 'freetype2'
--   found freetype2, version 17.1.11
-- Found Freetype: /usr/lib/x86_64-linux-gnu/libfreetype.so (found version "17.1.11") 
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:108 (message):
  Could NOT find PythonLibsUnix (missing: PYTHON_LIBRARY PYTHON_LIBPATH
  PYTHON_INCLUDE_DIR PYTHON_INCLUDE_CONFIG_DIR)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:315 (_FPHSA_FAILURE_MESSAGE)
  build_files/cmake/Modules/FindPythonLibsUnix.cmake:182 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:601 (find_package)




-- Configuring incomplete, errors occurred!
See also "/home/gregpayne/sc/Blender cycles/build_linux/CMakeFiles/CMakeOutput.log".
make: *** [all] Error 1
gregpayne@payne-MS-7522:~/sc/Blender cycles/blender-git-bake-cycles$


I have since resolved this.

1. Installed the Nvidia toolkik
2. Ran the install deps script as shown on [http://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Linux/Ubuntu/CMake](http://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Linux/Ubuntu/CMake) making sure to add the option it suggests when you run the script.
3. used the cmake GUI took to change the python version from 3.3 to 3.4
4. Added the flags suggested by teh dependencies script
5. configured and wrote the make files
6. make
7 make install.

---

### Post by Richard_Hainsworth on 2014-11-28
Same problem

The link ([http://wiki.blender.org/index.php/De...x/Ubuntu/CMake]("http://wiki.blender.org/index.php/Dev:grin:oc/Building_Blender/Linux/Ubuntu/CMake")) with all the information is invalid

What exactly did you do?

---

### Post by monkeybrain20122 on 2014-11-28
Blender doesn't need compile. Just download the latest Linux binary tarball, extract, click and that's it.

---


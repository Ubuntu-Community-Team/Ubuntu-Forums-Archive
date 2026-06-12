---
title: "CMake errors... I'm lost"
date: 2012-09-17
forum: Packaging and Compiling Programs
---

### Post by hubbardglutch on 2012-09-17
Hello, I am trying to install OpenGazer ([https://github.com/opengazer/OpenGazer](https://github.com/opengazer/OpenGazer)) to test for possible use by a student with cerebral palsy.  This program requires VXL, which requires a manual install/build.  I am attempting to follow the directions posted here ([http://vxl.sourceforge.net/releases/install-release.html](http://vxl.sourceforge.net/releases/install-release.html)), which involves using CMake.  I have never used CMake, and am running into a lot of errors.  I have searched around and seem to have taken care of a number of the errors by installing build-essential.

Here is what happens:  I open terminal in the bin directory parallel to the vxl source directory (vxl-1.14.0).  I type this in console 

```
cmake ../vxl-1.14.0
```here is the response I get:

```
Warning: turning off implicit template instantiation
-- Could NOT find DC1394 (missing:  DC1394_LIBRARIES DC1394_INCLUDE_DIR) 
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Could NOT find AVIFile (missing:  AVIFILE_INCLUDE_DIR AVIFILE_AVIPLAY_LIBRARY) 
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
NOT LINUX
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Found Open Cl? NO
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Could NOT find DIRECTSHOW (missing:  DIRECTX_INCLUDE_DIR DIRECTSHOW_INCLUDE_DIR DIRECTSHOW_STRMIIDS_LIBRARY DIRECTSHOW_QUARTZ_LIBRARY DIRECTSHOW_SOURCE_COMPILES)
-- Found Open Cl? NO
-- Configuring done
-- Generating done
-- Build files have been written to: /home/<user>/Desktop/vxl/vxl-1.14.0

```One interesting result is that instead of writing the build files to the parallel bin directory in which the terminal is open, it writes it to the source directory.  Also, I have searched a bit for directshow, and thought installing gstreamer may solve that issue.  But it did not.  

Any help you can give me would be great.  Thank you!

---

### Post by steeldriver on 2012-09-17
**DISCLAIMER: I have no idea what I'm doing - I just checked this out and tried to build it to see if I could help out**

First, **are you sure you need to build vxl from source? **At least in Precise, the repo appears to contain 1.14.0-14

```
$ apt-cache policy libvxl1-dev
libvxl1-dev:
  Installed: 1.14.0-14
  Candidate: 1.14.0-14
  Version table:
 *** 1.14.0-14 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
        100 /var/lib/dpkg/status

```If you really do need to build, it worked for me after doing the following:

1. get the prerequisites listed on the opengazer page [https://github.com/opengazer/OpenGazer](https://github.com/opengazer/OpenGazer) (it's not clear which are prereqs for VXL and which for opengazer)

```
sudo apt-get install libcv-dev libhighgui-dev libcvaux-dev libgtkmm-2.4-dev libcairomm-1.0-dev libboost-dev 
```2. make the source and bin dirs

```
$ mkdir -p ~/src/vxl/vxl-1.14/
$ mkdir ~/src/vxl/vxl-1.14/bin
```3. download the vxl source

```
$ cd /src/vxl/vxl-1.14/
$ svn co https://vxl.svn.sourceforge.net/svnroot/vxl/trunk
```4. export the VXLSRC variable

```
$ export VXLSRC=~/src/vxl/vxl-1.14/trunk/
```5. enter the bin dir and run cmake

```
$ cd ~/src/vxl/vxl-1.14/bin
$ cmake -i $VXLSRC

```It asked if I wanted to see advanced options and I said 'yes' because the opengazer web page says to set BUILD_SHARED_LIBS ON; I clicked through all the other options accepting the defaults apart from that one (there are lots!)

The 'make' then ran - successfully I think however I have not tested anything. It took a LOOOONG time (probably over an hour on a 32-bit VM inside my Core i5 Win7 box).

Hope this helps

---

### Post by hubbardglutch on 2012-09-18
First of all, thanks for checking this out and taking the time to do a little step-by-step.  I am definitely slowly expanding my understanding of the inner workings computers and programs.

I got all the way to the end, and then ran into something else.  After typing the cmake command, I got this response:

```
Would you like to see advanced options? [No]:y
Please wait while cmake processes CMakeLists.txt files....

CMake Error: The source directory "/home/hubbardglutch/src/vxl/bin" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

```I tried to solve this issue by copying the CMakeLists.txt file from the trunk directory into the bin directory.  This did seem to do something, but then I got pretty lengthy response.  This time, it couldn't find a lot of stuff.  I was able to go through quite a few options, but never came to the option I needed to change.  Ultimately, it was not successful.  Here is the very long response:

```
Would you like to see advanced options? [No]:y
Please wait while cmake processes CMakeLists.txt files....

CMake Error at CMakeLists.txt:26 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/VXLStandardOptions.cmake


CMake Error at CMakeLists.txt:27 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/config/vxl_utils.cmake


CMake Error at CMakeLists.txt:29 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/doxygen/doxygen.cmake


CMake Error: File /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/UseVXL.cmake does not exist.
CMake Error at CMakeLists.txt:35 (CONFIGURE_FILE):
  configure_file Problem configuring file


CMake Error: File /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/CTestCustom.cmake does not exist.
CMake Error at CMakeLists.txt:39 (CONFIGURE_FILE):
  configure_file Problem configuring file


CMake Error at CMakeLists.txt:82 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: config/cmake/config does not
  exists.


CMake Error at CMakeLists.txt:142 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: core does not exists.


CMake Error at CMakeLists.txt:202 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: config/cmake/export does not
  exists.




Variable Name: BUILD_CORE_GEOMETRY
Description: Build VXL's geometry libraries
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: BUILD_CORE_IMAGING
Description: Build VXL's imaging libraries
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: BUILD_CORE_NUMERICS
Description: Build VXL's numerics libraries
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: BUILD_CORE_PROBABILITY
Description: Build VXL's probability libraries (Experimental)
Current Value: OFF
New Value (Enter to keep current value): 

Variable Name: BUILD_CORE_SERIALISATION
Description: Build VXL's serialisation libraries
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: BUILD_CORE_UTILITIES
Description: Build VXL's utility libraries
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: BUILD_FOR_VXL_DASHBOARD
Description: Is this a build for the dashboard?
Current Value: OFF
New Value (Enter to keep current value): 

Variable Name: BUILD_UNMAINTAINED_LIBRARIES
Description: Build libraries that are no longer actively maintained?
Current Value: OFF
New Value (Enter to keep current value): 

Variable Name: CMAKE_AR
Description: Path to a program.
Current Value: /usr/bin/ar
New Value (Enter to keep current value): 

Variable Name: CMAKE_BACKWARDS_COMPATIBILITY
Description: For backwards compatibility, what version of CMake commands and syntax should this version of CMake try to support.
Current Value: 2.4
New Value (Enter to keep current value): 

Variable Name: CMAKE_BUILD_TYPE
Description: Choose the type of build, options are: None(CMAKE_CXX_FLAGS or CMAKE_C_FLAGS used) Debug Release RelWithDebInfo MinSizeRel.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_COLOR_MAKEFILE
Description: Enable/Disable color output during build.
Current Value: ON
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_COMPILER
Description: CXX compiler.
Current Value: /usr/bin/c++
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_FLAGS
Description: Flags used by the compiler during all build types.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_FLAGS_DEBUG
Description: Flags used by the compiler during debug builds.
Current Value: -g
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_FLAGS_MINSIZEREL
Description: Flags used by the compiler during release minsize builds.
Current Value: -Os -DNDEBUG
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_FLAGS_RELEASE
Description: Flags used by the compiler during release builds (/MD /Ob1 /Oi /Ot /Oy /Gs will produce slightly less optimized but smaller files).
Current Value: -O3 -DNDEBUG
New Value (Enter to keep current value): 

Variable Name: CMAKE_CXX_FLAGS_RELWITHDEBINFO
Description: Flags used by the compiler during Release with Debug Info builds.
Current Value: -O2 -g
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_COMPILER
Description: C compiler.
Current Value: /usr/bin/gcc
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_FLAGS
Description: Flags used by the compiler during all build types.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_FLAGS_DEBUG
Description: Flags used by the compiler during debug builds.
Current Value: -g
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_FLAGS_MINSIZEREL
Description: Flags used by the compiler during release minsize builds.
Current Value: -Os -DNDEBUG
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_FLAGS_RELEASE
Description: Flags used by the compiler during release builds (/MD /Ob1 /Oi /Ot /Oy /Gs will produce slightly less optimized but smaller files).
Current Value: -O3 -DNDEBUG
New Value (Enter to keep current value): 

Variable Name: CMAKE_C_FLAGS_RELWITHDEBINFO
Description: Flags used by the compiler during Release with Debug Info builds.
Current Value: -O2 -g
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXE_LINKER_FLAGS
Description: Flags used by the linker.
Current Value:  
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXE_LINKER_FLAGS_DEBUG
Description: Flags used by the linker during debug builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXE_LINKER_FLAGS_MINSIZEREL
Description: Flags used by the linker during release minsize builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXE_LINKER_FLAGS_RELEASE
Description: Flags used by the linker during release builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXE_LINKER_FLAGS_RELWITHDEBINFO
Description: Flags used by the linker during Release with Debug Info builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_EXPORT_COMPILE_COMMANDS
Description: Enable/Disable output of compile commands during generation.
Current Value: OFF
New Value (Enter to keep current value): 

Variable Name: CMAKE_INSTALL_PREFIX
Description: Install path prefix, prepended onto install directories.
Current Value: /usr/local
New Value (Enter to keep current value): 

Variable Name: CMAKE_LINKER
Description: Path to a program.
Current Value: /usr/bin/ld
New Value (Enter to keep current value): 

Variable Name: CMAKE_MAKE_PROGRAM
Description: Path to a program.
Current Value: /usr/bin/make
New Value (Enter to keep current value): 

Variable Name: CMAKE_MODULE_LINKER_FLAGS
Description: Flags used by the linker during the creation of modules.
Current Value:  
New Value (Enter to keep current value): 

Variable Name: CMAKE_MODULE_LINKER_FLAGS_DEBUG
Description: Flags used by the linker during debug builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_MODULE_LINKER_FLAGS_MINSIZEREL
Description: Flags used by the linker during release minsize builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_MODULE_LINKER_FLAGS_RELEASE
Description: Flags used by the linker during release builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_MODULE_LINKER_FLAGS_RELWITHDEBINFO
Description: Flags used by the linker during Release with Debug Info builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_NM
Description: Path to a program.
Current Value: /usr/bin/nm
New Value (Enter to keep current value): 

Variable Name: CMAKE_OBJCOPY
Description: Path to a program.
Current Value: /usr/bin/objcopy
New Value (Enter to keep current value): 

Variable Name: CMAKE_OBJDUMP
Description: Path to a program.
Current Value: /usr/bin/objdump
New Value (Enter to keep current value): 

Variable Name: CMAKE_RANLIB
Description: Path to a program.
Current Value: /usr/bin/ranlib
New Value (Enter to keep current value): 

Variable Name: CMAKE_SHARED_LINKER_FLAGS
Description: Flags used by the linker during the creation of dll's.
Current Value:  
New Value (Enter to keep current value): 

Variable Name: CMAKE_SHARED_LINKER_FLAGS_DEBUG
Description: Flags used by the linker during debug builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_SHARED_LINKER_FLAGS_MINSIZEREL
Description: Flags used by the linker during release minsize builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_SHARED_LINKER_FLAGS_RELEASE
Description: Flags used by the linker during release builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_SHARED_LINKER_FLAGS_RELWITHDEBINFO
Description: Flags used by the linker during Release with Debug Info builds.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: CMAKE_SKIP_RPATH
Description: If set, runtime paths are not added when using shared libraries.
Current Value: NO
New Value (Enter to keep current value): 

Variable Name: CMAKE_STRIP
Description: Path to a program.
Current Value: /usr/bin/strip
New Value (Enter to keep current value): 

Variable Name: CMAKE_USE_RELATIVE_PATHS
Description: If true, cmake will use relative paths in makefiles and projects.
Current Value: OFF
New Value (Enter to keep current value): 

Variable Name: CMAKE_VERBOSE_MAKEFILE
Description: If this value is on, makefiles will be generated without the .SILENT directive, and all commands will be echoed to the console during the make.  This is useful for debugging only. With Visual Studio IDE projects all commands are done without /nologo.
Current Value: FALSE
New Value (Enter to keep current value): 

Variable Name: EXECUTABLE_OUTPUT_PATH
Description: Single output directory for building all executables.
Current Value: 
New Value (Enter to keep current value): 

Variable Name: LIBRARY_OUTPUT_PATH
Description: Output directory for the vxl libraries
Current Value: /home/hubbardglutch/src/vxl/bin/lib
New Value (Enter to keep current value): 

Variable Name: VXL_EXTRA_CMAKE_CXX_FLAGS
Description: Extra flags appended to CMAKE_CXX_FLAGS
Current Value: 
New Value (Enter to keep current value): 

Variable Name: VXL_EXTRA_CMAKE_C_FLAGS
Description: Extra flags appended to CMAKE_C_FLAGS
Current Value: 
New Value (Enter to keep current value): 

Variable Name: VXL_EXTRA_CMAKE_EXE_LINKER_FLAGS
Description: Extra flags appended to CMAKE_EXE_LINKER_FLAGS
Current Value: 
New Value (Enter to keep current value): 

Variable Name: VXL_EXTRA_CMAKE_MODULE_LINKER_FLAGS
Description: Extra flags appended to CMAKE_MODULE_LINKER_FLAGS
Current Value: 
New Value (Enter to keep current value): 

Variable Name: VXL_EXTRA_CMAKE_SHARED_LINKER_FLAGS
Description: Extra flags appended to CMAKE_SHARED_LINKER_FLAGS
Current Value: 
New Value (Enter to keep current value): 

Variable Name: VXL_LEGACY_ERROR_REPORTING
Description: Use old error reporting methods rather than exceptions?
Current Value: ON
New Value (Enter to keep current value): 

Please wait while cmake processes CMakeLists.txt files....

CMake Error at CMakeLists.txt:26 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/VXLStandardOptions.cmake


CMake Error at CMakeLists.txt:27 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/config/vxl_utils.cmake


CMake Error at CMakeLists.txt:29 (INCLUDE):
  include could not find load file:

    /home/hubbardglutch/src/vxl/bin/config/cmake/doxygen/doxygen.cmake


CMake Error: File /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/UseVXL.cmake does not exist.
CMake Error at CMakeLists.txt:35 (CONFIGURE_FILE):
  configure_file Problem configuring file


CMake Error: File /home/hubbardglutch/src/vxl/bin/config/cmake/Modules/CTestCustom.cmake does not exist.
CMake Error at CMakeLists.txt:39 (CONFIGURE_FILE):
  configure_file Problem configuring file


CMake Error at CMakeLists.txt:82 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: config/cmake/config does not
  exists.


CMake Error at CMakeLists.txt:142 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: core does not exists.


CMake Error at CMakeLists.txt:202 (SUBDIRS):
  subdirs Incorrect SUBDIRS command.  Directory: config/cmake/export does not
  exists.
```Thanks for giving it a try!

---

### Post by oldos2er on 2012-09-18
Moved to Packaging and Compiling Programs.

---

### Post by steeldriver on 2012-09-18
Well I would go back and check the cmake output - it seems like you have something that's not being configured correctly

If I were you I would

1. install libvxl1-dev from the repo

2. attempt to build opengazer

There appear to be a couple of opengazer build issues; i.e.

[LIST=1]
[*][COMPILE ERROR] conflicting definition of 'exception' in PointTracker.h - you can fix that by editing the file and adding the namespace std:: explicitly
[*][LINK ERRORS - MULTIPLE] the Makefile places the libraries BEFORE the prerequisites - you can fix that by moving '$^'
[/LIST]
```
$ diff PointTracker.h.bak PointTracker.h
11c11
< class TrackingException: public exception {};
---
> class TrackingException: public std::exception {};


$ diff Makefile.bak Makefile
3c3
< VXLDIR = /opt
---
> VXLDIR = /usr
27c27
<     g++ $(CPPFLAGS) -o $@ `pkg-config cairomm-1.0 opencv gtkmm-2.4 --libs`  $(LINKER) $^
---
>     g++ $(CPPFLAGS) -o $@ $^ `pkg-config cairomm-1.0 opencv gtkmm-2.4 --libs`  $(LINKER)
40c40



```This was enough to get opengazer to compile and link - I can't test it (don't even have a camera). If it doesn't work then you can go back and fight with the vxl build.

Good luck

---


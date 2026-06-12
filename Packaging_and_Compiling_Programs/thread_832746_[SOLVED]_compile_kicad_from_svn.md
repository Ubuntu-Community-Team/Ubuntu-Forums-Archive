---
title: "[SOLVED] compile kicad from svn"
date: 2008-06-18
forum: Packaging and Compiling Programs
---

### Post by bschleusner on 2008-06-18
I tried to compile kicad today from source (svn) and it keeps failing on me. As far as I know I have all the prerequisites installed, but I think it has something to do with the way I am trying to compile.

First I downloaded it
```
svn checkout https://kicad.svn.sourceforge.net/svnroot/kicad/trunk/kicad kicad

```

then I made a directory called "build/release" in the folder and tried to do a cmake of it.

```
brad@badwulf:~/Desktop/svn/kicad/build/release$ cmake -DCMAKE_BUILD_TYPE=Release ../../
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Check for installed OpenGL -- found
-- Check for installed Boost -- found
-- Check for installed wxWidgets -- found
CMake Error: Error in cmake code at
/home/brad/Desktop/svn/kicad/cvpcb/CMakeLists.txt:81:
INSTALL TARGETS given unknown argument "BUNDLE".
Current CMake stack: 
[1]	/home/brad/Desktop/svn/kicad/cvpcb/CMakeLists.txt
CMake Error: Error in cmake code at
/home/brad/Desktop/svn/kicad/eeschema/CMakeLists.txt:127:
INSTALL TARGETS given unknown argument "BUNDLE".
Current CMake stack: 
[1]	/home/brad/Desktop/svn/kicad/eeschema/CMakeLists.txt
CMake Error: Error in cmake code at
/home/brad/Desktop/svn/kicad/gerbview/CMakeLists.txt:84:
INSTALL TARGETS given unknown argument "BUNDLE".
Current CMake stack: 
[1]	/home/brad/Desktop/svn/kicad/gerbview/CMakeLists.txt
CMake Error: Error in cmake code at
/home/brad/Desktop/svn/kicad/kicad/CMakeLists.txt:37:
INSTALL TARGETS given unknown argument "BUNDLE".
Current CMake stack: 
[1]	/home/brad/Desktop/svn/kicad/kicad/CMakeLists.txt
-- Check for installed zlib -- found
CMake Error: Error in cmake code at
/home/brad/Desktop/svn/kicad/pcbnew/CMakeLists.txt:173:
INSTALL TARGETS given unknown argument "BUNDLE".
Current CMake stack: 
[1]	/home/brad/Desktop/svn/kicad/pcbnew/CMakeLists.txt
-- Configuring done
```

What is "BUNDLE" and why is it doing this? Thanks in advance!

---

### Post by natros on 2008-06-19
can you post which version of cmake are you using. iirc the BUNDLE keyword is only supported for cmake >= 2.6.0, and afaik the keyword BUNDLE only makes sense to Mac OS X.

---

### Post by bschleusner on 2008-06-19
Thanks, thats all it was. I was using the old 2.4 version. :D

---


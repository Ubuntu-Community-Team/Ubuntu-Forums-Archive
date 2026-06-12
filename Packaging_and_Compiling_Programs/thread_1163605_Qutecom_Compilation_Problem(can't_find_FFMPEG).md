---
title: "Qutecom Compilation Problem(can't find FFMPEG)"
date: 2009-05-18
forum: Packaging and Compiling Programs
---

### Post by altobeta on 2009-05-18
i have download SIP Qutecom 2.2 and try to compile it on my ubuntu. I try to follow the instruction but it give me an error.

i try to "cmake -DCMAKE_BUILD_TYPE=Debug .."

> 
abort: There is no Mercurial repository here (.hg not found)
-- OS: Linux-2.6.27-11-generic
-- Processor: i686
-- Compiler: /usr/bin/gcc
-- Build type: Debug
-- Build tool: /usr/bin/gmake
-- Build directory: /home/amir/Desktop/qutecom-2-2-b816aa35e47c/build/debug
-- svn revision: 
-- Time: 20090519093304
Doing find_package(PkgConfig)
_AVCODEC_INCLUDEDIR = /usr/include
_AVCODEC_LIBDIR = /usr/lib
_AVCODEC_LIBS = avcodec;raw1394;theora;vorbisenc;avutil;vorbis;m;ogg
_AVCODEC_LIBS_L = 
_AVCODEC_LIBS_PATH = 
AVCODEC_INCLUDE_DIR = /usr/include/ffmpeg
CMake Error at owbuild/FindFFMPEG.cmake:266 (message):
  Could not find FFMPEG
Call Stack (most recent call first):
  libs/3rdparty/ffmpeg/CMakeLists-external.txt:2 (find_package)
  libs/3rdparty/ffmpeg/CMakeLists.txt:10 (include)


-- Configuring incomplete, errors occurred!



how to resolve this can't  find ffmpeg error,i have already check the file , it exist in /usr/include


regards
altobeta

---

### Post by foresto on 2009-05-19
I compiled it using the source package from the Karmic repository:

[http://packages.ubuntu.com/source/karmic/qutecom](http://packages.ubuntu.com/source/karmic/qutecom)

A backport request has been filed for Jaunty, so with some luck, if might be available in the repos before long:

[https://bugs.launchpad.net/jaunty-backports/+bug/377644](https://bugs.launchpad.net/jaunty-backports/+bug/377644)

---

### Post by altobeta on 2009-05-20
thanks for your reply
still no luck . i already  go to the link..  download the sources and try to compile it. It still give me the same error "can't find FFMPEG".

can u give me your step how u compile it??
i have already follow the instruction given but it still error

---

### Post by sadys on 2009-07-03
this link may be usefull
[http://lists.qutecom.org/pipermail/qutecom-dev/2009-May/001503.html](http://lists.qutecom.org/pipermail/qutecom-dev/2009-May/001503.html)
try edit CMakeCache.txt

---


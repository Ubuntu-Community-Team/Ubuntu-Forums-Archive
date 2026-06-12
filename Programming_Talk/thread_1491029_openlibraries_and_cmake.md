---
title: "openlibraries and cmake"
date: 2010-05-23
forum: Programming Talk
---

### Post by newsman on 2010-05-23
The openlibraries project has instructions for building it in ubuntu 8

([http://openlibraries.org/wiki/BuildingUbuntuEight](http://openlibraries.org/wiki/BuildingUbuntuEight))

It mentions
> As referenced in  [http://lists.openlibraries.org/pipermail/developers/2008-June/000008.html](http://lists.openlibraries.org/pipermail/developers/2008-June/000008.html)  , Ubuntu 8.04 does not ship the required version of CMake. Please install the intrepid version. (Available from archive.ubuntu.com ) 

I want to avoid that if possible...

Anywho (needless to say) I cannot compile it but i think its nothing to do with this.

It says in the instruction link: 

cmake ../<path_to_src> -DWITH_PYTHON_EXTENTIONS:BOOL=TRUE
make
sudo make install


This gives error and besides I think there is a typo as well... The error first is..
```
cmake ../openlibraries/ -DWITH_PYTHON_EXTENTIONS:BOOL=TRUE
defining plugin paths
-- Boost version: 1.40.0
-- Found the following Boost libraries:
--   filesystem
--   regex
--   thread
--   iostreams
found boost: /usr/include
found LibXml2: /usr/include/libxml2
found OpenGL: /usr/include
found GLEW: /usr/include/GL
Found Python: /usr/include/python2.6 /usr/lib/libpython2.6.so 
Found libJPEG: /usr/lib/libjpeg.so /usr/include
-- Could NOT find OpenEXR  (missing:  OpenEXR_INCLUDE_DIR)
Can't find libopenexr. Skipping OpenEXR plugin.
CMake Warning (dev) at src/openimagelib/plugins/CMakeLists.txt:18 (add_subdirectory):
  The source directory

    /home/xpert/openlibraries/src/openimagelib/plugins/tiff

  does not contain a CMakeLists.txt file.

  CMake does not support this case but it used to work accidentally and is
  being allowed for compatibility.

  Policy CMP0014 is not set: Input directories must have CMakeLists.txt.  Run
  "cmake --help-policy CMP0014" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.

Found Python: /usr/include/python2.6 /usr/lib/libpython2.6.so 
found GLUT: /usr/include
-- checking for module 'libavdevice'
--   package 'libavdevice' not found
checking: avformat.h
found: /usr/include/libavformat
checking: avcodec.h
found: /usr/include/libavcodec
checking: avutil.h
found: /usr/include/libavutil
checking: avdevice.h
checking: swscale.h
found: /usr/include/libswscale
CMake Error at FindFFMPEG.cmake:85 (LIST):
  list sub-command REMOVE_DUPLICATES requires list to be present.
Call Stack (most recent call first):
  src/openmedialib/plugins/avformat/CMakeLists.txt:2 (find_package)


failed to find FFMPEG: try setting FFMPEGDIR
libopenfx not found. Skipping libopenfx plugin.
found OpenAL: /usr/include/AL
found SDL: /usr/include/SDL
Found Python: /usr/include/python2.6 /usr/lib/libpython2.6.so 
CMake Warning (dev) at src/openassetlib/CMakeLists.txt:2 (add_subdirectory):
  The source directory

    /home/xpert/openlibraries/src/openassetlib/plugins

  does not contain a CMakeLists.txt file.

  CMake does not support this case but it used to work accidentally and is
  being allowed for compatibility.

  Policy CMP0014 is not set: Input directories must have CMakeLists.txt.  Run
  "cmake --help-policy CMP0014" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Warning (dev) at src/openobjectlib/CMakeLists.txt:5 (add_subdirectory):
  The source directory

    /home/xpert/openlibraries/src/openobjectlib/plugins

  does not contain a CMakeLists.txt file.

  CMake does not support this case but it used to work accidentally and is
  being allowed for compatibility.

  Policy CMP0014 is not set: Input directories must have CMakeLists.txt.  Run
  "cmake --help-policy CMP0014" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
Boost_FILESYSTEM_LIBRARY (ADVANCED)
    linked by target "openmedialib_glew" in directory /home/xpert/openlibraries/src/openmedialib/plugins/glew
    linked by target "openmedialib_gensys" in directory /home/xpert/openlibraries/src/openmedialib/plugins/gensys

-- Configuring incomplete, errors occurred!

```

There is also a typo I believe as in the install document
```

If running cmake from the command line, some useful options to pass to are:
 * -G "NMake Makefiles": generates makefiles for nmake
 * -D CMAKE_INSTALL_PREFIX:STRING=c:\openlibraries 
 * -D CMAKE_BUILD_TYPE:STRING=Release 
 * -D WITH_PYTHON_EXTENSIONS:BOOL=FALSE
 * -D WITH_OPENFX_PLUGIN:BOOL [default is FALSE]
 * -D WITH_OPENML:BOOL [default is TRUE] 
 * -D WITH_OPENIL:BOOL [default is TRUE] 
 * -D WITH_OPENAL:BOOL [default is TRUE] 
 * -D WITH_OPENFXL:BOOL [default is FALSE] 
 * -D WITH_OPENOL:BOOL [default is TRUE] 
 * -D WITH_POOL:BOOL [default is TRUE]

```


Now if we were to correct the typo i get a directory error instead

```


cmake ../openlibraries/ -D WITH_PYTHON_EXTENSIONS:BOOL=TRUE
CMake Error: The source directory "/home/xpert/olib_build/WITH_PYTHON_EXTENSIONS:BOOL=TRUE" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.

```

---

### Post by rCXer on 2010-05-23
According to the [cmake's man page]("http://linux.die.net/man/1/cmake"), the syntax is...
```

cmake [options] <path-to-source>

```

Have you tried...
```

cmake -D WITH_PYTHON_EXTENSIONS:BOOL=TRUE ../openlibraries/

```

---


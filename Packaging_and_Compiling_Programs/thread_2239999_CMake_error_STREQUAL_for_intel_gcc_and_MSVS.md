---
title: "CMake error STREQUAL for intel gcc and MSVS"
date: 2014-08-17
forum: Packaging and Compiling Programs
---

### Post by akimb0 on 2014-08-17
Im trying to compile an open source plugin for maya and was able to solve all dependencies but recieve an error message when make install:

```
$ sudo make install
CMake Error at maya/plugin/src/CMakeLists.txt:51 (if):
  if given arguments:

    "STREQUAL" "intel"

  Unknown arguments specified


-- Configuring incomplete, errors occurred!
make: *** [cmake_check_build_system] Error 1
```

I checked the maya/plugin/src/CMakeLists.txt file and here i have three sections about additional compiler flags:

```
# special Intel link flags

if ($ENV{EM_COMPILER} STREQUAL "intel")
target_link_libraries(naiadBuddyForMaya${MAYA_VERSION} -Bsymbolic)
set(EMLIBS Nb${EM_D})
endif ($ENV{EM_COMPILER} STREQUAL "intel")

# special gcc link flags

if ($ENV{EM_COMPILER} STREQUAL "gcc")
target_link_libraries(naiadBuddyForMaya${MAYA_VERSION} -symbolic)
set(EMLIBS Nb${EM_D})
endif ($ENV{EM_COMPILER} STREQUAL "gcc")

# special MSVC link flags

if ($ENV{EM_COMPILER} STREQUAL "MSVC")
set_target_properties(naiadBuddyForMaya${MAYA_VERSION} PROPERTIES SUFFIX ".mll")
target_link_libraries(naiadBuddyForMaya${MAYA_VERSION} -symbolic)
set(EMLIBS Nb${EM_D})
endif ($ENV{EM_COMPILER} STREQUAL "MSVC")
```

I have no clue what "Unknown arguments specified" in the error message could mean.

If i delete this three sections from the CMakeList.txt cmake finishes but i got some symbol look up errors if i try to load the compiled plugin to maya so i guess this might be needed??

---

### Post by steeldriver on 2014-08-17
I don't really speak Cmake, but the way I would interpret that error is that the EM_COMPILER variable is empty (undefined) causing the statement

```

if ($ENV{EM_COMPILER} STREQUAL "intel")

```

to expand to
```

if ( STREQUAL "intel")

```

You mention "Intel gcc and MSVS" in your title - which compiler are you actually using? Can you list the steps leading up to the 'make install' command (or link to the instructions you're following)?

---

### Post by akimb0 on 2014-08-17
Well im using gcc at the moment where 
```
$ echo $EM_COMPILER
``` 
gives me a 
```
$ gcc
``` 
so shouldnt this work and jump to the second if loop with gcc??

Yes sure, the sorce is available here [https://github.com/BlackGinger/Naiad-Buddies/tree/master/maya](https://github.com/BlackGinger/Naiad-Buddies/tree/master/maya)
The instructions i followed are on the page above.

Like i said if i uncomment the additional compiler flags it works, but results in missing symbols...

---

### Post by steeldriver on 2014-08-17
How/where did you set the value of EM_COMPILER? is it just in the current shell or did you export it? What does

```

sh -c 'echo $EM_COMPILER'

```

say? 

I assume you successfully ran cmake in the build directory, right?

---

### Post by akimb0 on 2014-08-17
Its in the current shell ```
$ sh -c 'echo $EM_COMPILER'
gcc
```

Im not 100 percent following the instructions as ```
git clone  git://github.com/ExoticMatter/Naiad-Buddy-For-Maya.git naiad_buddy_src
Cloning into 'naiad_buddy_src'...
fatal: remote error: 
  Repository not found.
```
Is not longer working.

However in short i did the following:

```
cd /usr/ExoticMatter/Naiad/src
unzip Naiad-Buddies-master.zip
cd Naiad-Buddies-master/
```
gedit CMakeLists.txt ***and change "subdirs (arnold houdini maya krakatoa renderman vray)" to "subdirs (maya)"***
```
export EM_COMPILER=gcc
export CC=gcc
export CXX=g++
export EM_PLAT=LINUX
export EM_ARCH=`uname -m`
export NAIAD_PATH=/usr/ExoticMatter/Naiad
cmake -DCMAKE_BUILD_TYPE=RELEASE  -DMAYA_INSTALL_PATH=/usr/autodesk/maya2014-x64 -DMAYA_VERSION=2014  -DCMAKE_INSTALL_PREFIX=$NAIAD_PATH
-- The C compiler identification is GNU 4.8.2
-- The CXX compiler identification is GNU 4.8.2
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/g++
-- Check for working CXX compiler: /usr/bin/g++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so - found
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
-- Found X11: /usr/lib/x86_64-linux-gnu/libX11.so
-- Found OpenGL: /usr/lib/x86_64-linux-gnu/libGL.so  
-- Configuring done
-- Generating done
-- Build files have been written to: /usr/ExoticMatter/Naiad/src/Naiad-Buddies-master
sudo make install
CMake Error at maya/plugin/src/CMakeLists.txt:51 (if):
  if given arguments:

    "STREQUAL" "intel"

  Unknown arguments specified


-- Configuring incomplete, errors occurred!
make: *** [cmake_check_build_system] Error 1
```

---

### Post by steeldriver on 2014-08-17
I wonder if it's something as simple as sudo not preserving your environment? IMHO you shouldn't ever really need to use sudo to build stuff (only to install it after)

Personally I always download and build things in a directory that I have write permissions in as a normal user: either ~/src or /usr/local/src (which I've setup with group ownership 'staff' and setguid bit). **That way you can 'configure' (or 'cmake') and 'make' without sudo** - just using sudo for the final 'make install' (which is usually just a copying process).

---

### Post by akimb0 on 2014-08-17
Genius :-)
that did the trick (well im still curios about why this doesnt work with a sudo) the compiler starts with a bunch of messages and some warnings about 
```
...warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result [-Wunused-result]...
```

But im running into a new issue near the end of compiling:
```
g++: error: unrecognized command line option ‘-symbolic’
```

which seems to be related to 
```
if ($ENV{EM_COMPILER} STREQUAL "gcc")
target_link_libraries(naiadBuddyForMaya${MAYA_VERSION} [COLOR=#ff0000]**-symbolic**[/COLOR])
set(EMLIBS Nb${EM_D})
endif ($ENV{EM_COMPILER} STREQUAL "gcc")

```

so finally this error prevents a build success.

---

### Post by steeldriver on 2014-08-17
Sorry - I'm not familiar with that particular linker option

As for sudo, that's normal behavior (at least in the Ubuntu configuration) and is for security reasons

```

       By default, the env_reset option is enabled.  This causes commands to
       be executed with a minimal environment containing TERM, PATH, HOME,
       MAIL, SHELL, LOGNAME, USER and USERNAME in addition to variables from
       the invoking process permitted by the env_check and env_keep options.
       This is effectively a whitelist for environment variables.

```

See the 'Command environment' section of the sudoers manpage

---


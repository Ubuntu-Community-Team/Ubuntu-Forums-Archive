---
title: "Porting autoconf to cmake"
date: 2010-10-11
forum: Packaging and Compiling Programs
---

### Post by Colin@oxford on 2010-10-11
I am transferring the build system from the old autoconf tools to cmake.  Mostly this is fine, but there are some aspects that cmake does not appear to take into account.

Firstly the old configure scripts looked for argp.h and set HAVE_ARGP_H if found.  The source files used #ifdef HAVE_ARGP_H to protect the inclusion (I assume that systems that do not have argp.h have the appropriate declarations in some other header).  Now I can check this myself, but is there something already written that sets HAVE_ARGP_H?

Secondly, with KDE4 libraries, the flag -fvisibility=hidden is set, which means that by default all functions are local to the shared library being created.  I thus need to mark all exported functions with an appropriate attribute, but this is specific to GCC.  Is there anything that sets appropriate macros dependent on compiler/environment so that this will be portable?

---

### Post by MadCow108 on 2010-10-11
check_include_file(argp.h HAVE_ARGP_H -DHAVE_ARGP_H)
see cmake docs.

concerning the second. I guess other compilers/linkers have similar a flag, but I am not aware of a macro which does the correct checks.
You may have do some searching in the net and if not successful write one yourself (and publish it for the benefit of others :) )

the simple solution would be to disable the flag on non-gcc platforms as it is just an (in many cases negligible) efficiency flag

---

### Post by Colin@oxford on 2010-10-12
Thanks, but:

> 
CMake Error at CMakeLists.txt:25 (check_include_file):
  Unknown CMake command "check_include_file".


I can use "check_include_files", but that does not allow the setting of a compiler flag.  This is very odd, since I have both 

CheckIncludeFile.cmake

and

CheckIncludeFiles.cmake

in /usr/share/cmake-2.8/Modules

Any ideas?

---

### Post by MadCow108 on 2010-10-12
put this in an appropriate place
include(CheckIncludeFile)

---

### Post by Colin@oxford on 2010-10-13
Now this is weird.  My cmake file is:
```

cmake_minimum_required(VERSION 2.8)

include(CheckIncludeFile)
include(CheckIncludeFiles)
message("Trying check_include_file")
CHECK_INCLUDE_FILE(argp.h HAVE_ARGPH, HAVE_ARGP)
message("Trying check_include_files")
CHECK_INCLUDE_FILES(argp.h HAVE_ARGP_H)
if (HAVE_ARGP_H)
   message("Found argp.h")
   add_definitions(-DHAVE_ARGP)
else()
   message("argp.h not found")
endif()

```

And the result is:
> 
Trying check_include_file
-- Looking for argp.h
-- Looking for argp.h - not found
Trying check_include_files
-- Looking for include files HAVE_ARGP_H
-- Looking for include files HAVE_ARGP_H - found
Found argp.h


argp.h is sitting there in /usr/include.
Is this a bug in CheckIncludeFile?  Is that why KDE4 decides not to bring it in by default?

---


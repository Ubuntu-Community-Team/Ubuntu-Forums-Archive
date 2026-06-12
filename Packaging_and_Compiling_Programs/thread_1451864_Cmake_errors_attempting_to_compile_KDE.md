---
title: "Cmake errors attempting to compile KDE"
date: 2010-04-11
forum: Packaging and Compiling Programs
---

### Post by Colin@oxford on 2010-04-11
I want to build some KDE programs from source, so started from the instructions at [http://wiki.koffice.org/index.php?title=Building/Building_KOffice]("http://wiki.koffice.org/index.php?title=Building/Building_KOffice")

Specifically, I ran 

```
sudo apt-get build-dep koffice-kde4

```
to get all the dependencies. Then created a new directory into which I put the source using 
```

svn co svn://anonsvn.kde.org/home/kde/trunk/koffice

```
and created two directories "build" and "install".

In the build directory, I typed:

```
cmake -DCMAKE_INSTALL_PREFIX=../install/ ../koffice/ -DCMAKE_BUILD_TYPE=RefWithDebInfo

```
This gave two warnings saying that modules were not found, the first is:
```

CMake Warning at /usr/share/kde4/apps/cmake/modules/MacroOptionalFindPackage.cmake:19 (FIND_PACKAGE):
  Could not find module FindCreateResources.cmake or a configuration file for
  package CreateResources.

  Adjust CMAKE_MODULE_PATH to find FindCreateResources.cmake or set
  CreateResources_DIR to the directory containing a CMake configuration file
  for CreateResources.  The file will have one of the following names:

    CreateResourcesConfig.cmake
    createresources-config.cmake

Call Stack (most recent call first):
  CMakeLists.txt:153 (macro_optional_find_package)

```
and the second the same but for KofficeSqlite.  I do have SQLite installed on this machine, so I do not know what extra it is asking for.

However, I then get errors of the form:

```
CMake Error at CMakeLists.txt:468 (add_subdirectory):
  add_subdirectory given source "libs" which is not an existing directory.

```

and the same for "interfaces", "cmake", "pics" etc...

this stops cmake from progressing further.

What am I missing?

---

### Post by SevenMachines on 2010-04-11
assuming those directories exist in your koffice directory, try cmake without specifying the build dir 
$cmake -DCMAKE_INSTALL_PREFIX=../install/  -DCMAKE_BUILD_TYPE=RefWithDebInfo

the optional missing warning you mention is the create-resources package, which contains brushes and such

---

### Post by Colin@oxford on 2010-04-11
Those directories do not exist under koffice,

---

### Post by SevenMachines on 2010-04-11
they should do, your svn checkout must be incomplete for some reason, you might want to repeat it and see if it goes without error. the directories are fine here using the svn checkout you mention above

---

### Post by Colin@oxford on 2010-04-12
It seems that if I individually download those directories, all is OK.
I wonder why they were not found automatically.

---

### Post by Colin@oxford on 2010-04-12
I have re-run the svn command and all those directories have now appeared.  Very strange.

Now I want to build kexi as well, but this is currently blocked because it cannot find cmake files for sqlite.  The log suggests looking at [www.sqlite.org](www.sqlite.org) but there appears not to be a suitable cmake file in their archives, so where do I get the appropriate set of files from?

---

### Post by SevenMachines on 2010-04-12
with libsqlite3-dev installed you could try adding the options 

-DSQLITE_INCLUDE_DIR=/usr/include/ -DSQLITE_LIBRARIES=/usr/lib/libsqlite.so.0

to your cmake command. it seems to work but i have to warn that i know absolutely nothing about cmake (or even kde!) so it might not be the right way to go about it

---

### Post by Colin@oxford on 2010-04-12
Ah, yes.  I have not appreciated the difference between libsqlite0-dev and libsqlite3-dev.  The former is a dependency of kde-devel whreas the latter is required by kexi!  Works without the additional -D now.

---


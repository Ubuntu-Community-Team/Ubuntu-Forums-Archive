---
title: "using non standard library in Cmake"
date: 2014-12-04
forum: Packaging and Compiling Programs
---

### Post by monkeybrain20122 on 2014-12-04
Hi,

I am trying to build a program from source. I would like to use a local version of hdf5 (in $HOME/opt/hdf5)  to build it instead of the system version. The system version is installed (libhdf5-openmpi) but doesn't work for the program I am trying to build here because of openmpi (I need hdf5 with openmpi enabled for other programs)

I am wondering how to configure Cmake to 1) find the local version of hdf5 2) overrides the default and use it instead of the system version.

I think I am supposed to edit CMAkelist.txt but not sure how. Here are the entries that may be relevant

```
FIND_PACKAGE(HDF5)
IF (HDF5_FOUND)
    SET(HAVE_HDF5 1)
    LIST(APPEND DEFINES HAVE_HDF5)
    LIST(APPEND INCLUDES ${HDF5_INCLUDE_DIRS})
    SET(POSTLINKFLAGS ${POSTLINKFLAGS} ${HDF5_LIBRARIES})
ENDIF()


```

---

### Post by steeldriver on 2014-12-05
Have you tried running / grepping
```

cmake -LH

```

or
```

cmake -LAH

```

to see if there's a variable defined for hdf5? if so you may be able to override the default using a -D directive

---

### Post by monkeybrain20122 on 2014-12-05
Hi, cmake -LAH produces these outputs

```
// HDF5 C++ Wrapper compiler.  Used only to detect HDF5 compile flags.
HDF5_CXX_COMPILER_EXECUTABLE:FILEPATH=/usr/bin/h5c++

// HDF5 Wrapper compiler.  Used only to detect HDF5 compile flags.
HDF5_C_COMPILER_EXECUTABLE:FILEPATH=/usr/bin/h5cc

// Path to a file.
HDF5_C_INCLUDE_DIR:PATH=/usr/include

// HDF5 file differencing tool.
HDF5_DIFF_EXECUTABLE:FILEPATH=HDF5_DIFF_EXECUTABLE-NOTFOUND

// The directory containing a CMake configuration file for HDF5.
HDF5_DIR:PATH=HDF5_DIR-NOTFOUND

// HDF5 Fortran Wrapper compiler.  Used only to detect HDF5 compile flags.
HDF5_Fortran_COMPILER_EXECUTABLE:FILEPATH=/usr/bin/h5fc

// HDF5 library compiled with parallel IO support
HDF5_IS_PARALLEL:BOOL=TRUE

// Path to a library.
HDF5_dl_LIBRARY_DEBUG:FILEPATH=HDF5_dl_LIBRARY_DEBUG-NOTFOUND

// Path to a library.
HDF5_dl_LIBRARY_RELEASE:FILEPATH=/usr/lib/x86_64-linux-gnu/libdl.so

// Path to a library.
HDF5_hdf5_LIBRARY_DEBUG:FILEPATH=HDF5_hdf5_LIBRARY_DEBUG-NOTFOUND

// Path to a library.
HDF5_hdf5_LIBRARY_RELEASE:FILEPATH=/usr/lib/x86_64-linux-gnu/libhdf5.so

// Path to a library.
HDF5_m_LIBRARY_DEBUG:FILEPATH=HDF5_m_LIBRARY_DEBUG-NOTFOUND

// Path to a library.
HDF5_m_LIBRARY_RELEASE:FILEPATH=/usr/lib/x86_64-linux-gnu/libm.so

// Path to a library.
HDF5_pthread_LIBRARY_DEBUG:FILEPATH=HDF5_pthread_LIBRARY_DEBUG-NOTFOUND

// Path to a library.
HDF5_pthread_LIBRARY_RELEASE:FILEPATH=/usr/lib/x86_64-linux-gnu/libpthread.so

// Path to a library.
HDF5_z_LIBRARY_DEBUG:FILEPATH=HDF5_z_LIBRARY_DEBUG-NOTFOUND

// Path to a library.
HDF5_z_LIBRARY_RELEASE:FILEPATH=/usr/lib/x86_64-linux-gnu/libz.so
  for hdf5
```

Now how do I use the -D directive to override these so that program with compile with my local copy of hdf5 in $HOME/opt/hdf5? I am not very familiar with cmake. Thanks

---

### Post by slickymaster on 2014-12-05
*Moved to the ***Packaging and Compiling Programs*** sub-forum*

---

### Post by steeldriver on 2014-12-06
I don't know enough to advise you, however the cmake documentation seems to suggest that you can set an environment variable HDF5_ROOT

[http://www.cmake.org/cmake/help/v3.0/module/FindHDF5.html](http://www.cmake.org/cmake/help/v3.0/module/FindHDF5.html)

---

### Post by monkeybrain20122 on 2014-12-21
Ok. Figured it out. It is easier than I thought. :)
Instead of editing Cmake.txt just add the options  -DCMAKE_INCLUDE_PATH and -DCMAKE_LIBRARY_PATH to the cmake command and it works.

So to build out of source the command is 
```
cmake -DCMAKE_INCLUDE_PATH=$HOME/opt/hdf5/include -DCMAKE_LIBRARY_PATH=$HOME/opt/hdf5/lib  ..
```

---


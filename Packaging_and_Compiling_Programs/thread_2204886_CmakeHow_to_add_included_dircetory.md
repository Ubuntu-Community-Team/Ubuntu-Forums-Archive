---
title: "Cmake:How to add included dircetory?"
date: 2014-02-10
forum: Packaging and Compiling Programs
---

### Post by monkeybrain20122 on 2014-02-10
Hi, 

While compiling shogun (machine learning toolbox) with cmake I got this error
```
Building CXX object src/shogun/CMakeFiles/libshogun.dir/io/HDF5File.cpp.o
In file included from /usr/include/hdf5.h:24:0,
                 from /home/bee/Downloads/shogun-build/shogun/src/shogun/io/HDF5File.cpp:17:
/usr/include/H5public.h:63:20: fatal error: mpi.h: No such file or directory
 #   include "
```

 mpi.h is in /usr/lib/openmpi/include/mpi.h, I want to add this path to INCLUDES, but don't know how to do it in Cmake. Help would be appreciated.

---

### Post by monkeybrain20122 on 2014-02-16
Nobody use Cmake?

---

### Post by steeldriver on 2014-02-16
Have you tried 

```
cmake -LA | grep -i mpi
```

to see if there's a variable you can set to tell it the mpi install location (it's possibly something like -DWITH_MPI=/path/to/mpi )

---

### Post by andrew.46 on 2014-02-26
Or you could use ccmake for a decent look at *all *of the variables available to you. cmake is not installed with cmake, you will need to run:

```

sudo apt-get install cmake-curses-gui

```

You can see the exact syntax by trawling through the generated cache file (less the -D of course).

---


---
title: "Can anyone help with FLASH Code: make Error1 and hdf5"
date: 2016-06-09
forum: Packaging and Compiling Programs
---

### Post by priscila3 on 2016-06-09
Hi,
I'm trying to compile this Physics code named FLASH. These are the requirements:

1. F 90 and C compiler
2. Installed copy of Message-Passing interface (MPI)
3. HDF5
4. Parallel net CDF
5. GNU gmake
6. Python

I have successfully installed all of the above.
I'm getting the following error  (image attached)
This error happens when I do the 'make' command and starts compiling and then it stops with the message:

In file included from io_h5_attribute.h:7:0,
                 from io_attribute.h:13,
                 from io_attribute.c:1:
io_h5_type.h:7:18: fatal error: hdf5.h: No such file or directory
compilation terminated.
Makefile:123: recipe for target 'io_attribute.o' failed
make: *** [io_attribute.o] Error 1

Thank you in advance.

---

### Post by howefield on 2016-06-09
Thread moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by steeldriver on 2016-06-09
What packages did you install, exactly (and how)? in Ubuntu, there are separate development packages (different from the runtime library packages) e.g. libhdf5-dev for hdf5

---

### Post by priscila3 on 2016-06-09
Thanks, for replying. I did sudo apt-get install to the following:

libhdf5-mpi-dev
libhdf5-cpp-11:
libhdf5-doc
libhdf5-serial-dev

---

### Post by priscila3 on 2016-06-09
Ok I just found a typo on one of the paths of the makefile (sorry...) and I no  longer got the hdf5 error, but I still have this one: (screenshot  attached)
and I have no clue for this one. Thank you.

---

### Post by nikefalcon on 2016-06-17
It might help if you directed us to the webpage where the project is hosted, along with the source.

---


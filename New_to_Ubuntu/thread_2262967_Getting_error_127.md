---
title: "Getting error 127"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by jeevan3 on 2015-01-28
generating Makefile
SUCCESS
root@jeevan-Aspire-V7-482PG:/home/jeevan/Downloads/FLASH4.2.1# cd object
root@jeevan-Aspire-V7-482PG:/home/jeevan/Downloads/FLASH4.2.1/object# make
Calculating dependencies
./setup_depends.py --generateINTERMEDIATElines -ggdb -c -O2 -fdefault-real-8 -fdefault-double-8 -Wuninitialized  -I/usr/local/hdf5/include -DH5_USE_16_API -ggdb -c -O2 -Wuninitialized -D_FORTIFY_SOURCE=2 *.f *.f90 *.F90 *.F 
./setup_addcdepends.py -I/usr/local/hdf5/include -DH5_USE_16_API -ggdb -c -O2 -Wuninitialized -D_FORTIFY_SOURCE=2 *.c
rm -f reorder.sh
/usr/local/mpich2//bin/mpif90 -ggdb -c -O2 -fdefault-real-8 -fdefault-double-8 -Wuninitialized  -DMAXBLOCKS=1000 -DNXB=8 -DNYB=8 -DNZB=1 -DN_DIM=2 Burn_interface.F90
make: /usr/local/mpich2//bin/mpif90: Command not found
Makefile:115: recipe for target 'Burn_interface.o' failed
make: *** [Burn_interface.o] Error 127


[SIZE=3]Can anyone help me with this error. It has been killing me for days [/SIZE]

---

### Post by steeldriver on 2015-01-28
Well, it's expecting to find a MPI-enabled (parallel) Fortran compiler (mpif90) in /usr/local/mpich2/bin - is there one? if not where is it?

Perhaps take a step back and tell us what software you are trying to build and what preliminary steps (installing prerequisites, configuring build tools etc.) you have taken

---

### Post by jeevan3 on 2015-01-28
I am trying to insall a software named FLASH code. It has the following prerequisites:

1. F 90 and C compiler
2. Installed copy of Message-Passing interface (MPI)
3. HDF5
4. Parallel net CDF
5. GNU gmake
6. Python

root@jeevan-Aspire-V7-482PG:~# which mpif90
/home/jeevan/mpich-install/bin/mpif90

I havesuccessfully installed all the prerequisite software. The location of the mpif90 is shown as above. What can I do to run the program successfully. Thank you in advance.

---

### Post by steeldriver on 2015-01-28
You will need to figure out where the /usr/local/mpich2//bin/ path is coming from, I think

It may be hard-wired into the makefile, or (if the source package uses GNU autoconf) it may be deriving it from a ./configure script in which case look for a command-line option that allows you to override the default

---

### Post by jeevan3 on 2015-01-29
I make changes to the the Path of mpif90 in the make file and it worked. Thank you so much

---


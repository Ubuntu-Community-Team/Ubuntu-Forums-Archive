---
title: "Compilation error: FORTRAN missing C++ libraries"
date: 2014-08-17
forum: Packaging and Compiling Programs
---

### Post by cyclingchap on 2014-08-17
Hi,

I have just upgraded from 12.04 to 14.04, or rather I (wisely) performed a parallel install of Trusty next to Precise as I anticipated that Trusty would screw up many of my settings etc.

And lo it proved to be the case!!

Under 12.04 I ran the following makefile to compile a FORTRAN 90 code:

```
FC               =      mpif90
FL               =      $(FC)
# For debugging
# FCFLAGS          =      -l -g -fopenmp -fbacktrace -Wall -Warray-bounds -pedantic -xf95-cpp-input

# For performance
FCFLAGS          =      -l -p -g -fopenmp -O3 -xf95-cpp-input
FLFLAGS          =      -fopenmp 
EXEC             =      thermo

ZIPDIR           =      /home/user/Programs/zlib-1.2.7-bin
H5DIR            =      /home/user/Programs/hdf5-1.8.9-gfortran-bin
SILODIR          =      /home/user/Programs/silo-4.8-bin
PETSCDIR         =      /home/user/Programs/petsc-3.3-p5
PETSCDIR2        =      /home/user/Programs/petsc-3.3-p5/linux-gnu-mpi-debug
INCLUDE          =      -I $(H5DIR)/include -I $(SILODIR)/include -I $(ZIPDIR)/include -I $(PETSCDIR)/include -I $(PETSCDIR2)/include

LIB              =       $(SILODIR)/lib/libsiloh5.a \
                     $(H5DIR)/lib/libhdf5_fortran.a \
                     $(H5DIR)/lib/libhdf5.a \
                     $(ZIPDIR)/lib/libz.a \
                     $(PETSCDIR2)/lib/libpetsc.a \
                     $(PETSCDIR2)/lib/libflapack.a \
                     $(PETSCDIR2)/lib/libfblas.a \
                     -lstdc++

# List of required object files
OBJS             =          ./THERMO_transport.o \
                        ./theta_angle.o \
                        ./Quadrature_Data.o \
                        ./Sn_Eqn.o
                    
$(EXEC) : $(OBJS)
      $(FL) $(OBJS) $(FLFLAGS) $(LIB)  -o $(EXEC) 

%.o : %.f90
    $(FC) $(INCLUDE) $(FCFLAGS)  -c $<

```

This worked fine under 12.04. Note that I configured and installed all the libraries except the -lstdc++ library which I think (from memory) just worked without me doing anything special. I think that library is in /usr/libs ?

Anyway, in 14.04 on running the makefile I now get:

```
/usr/bin/ld: cannot find -lstdc++
```

So something's obviously changed, or I installed the relevant c++ libraries in 12.04 and have just forgotten how I did it.

Clearly the relevant library is missing or somewhere different to where it is in 12.04.

I've read loads of stuff about 32 bit libraries not being included in 14.04 and I have installed a bunch of libraries to no avail.

Anyone know what's going on here?

Cheers

---

### Post by steeldriver on 2014-08-17
Have you installed the build-essential metapackage? That should include g++, which in turn should pull in the appropriate libstdc++6-x.y-dev library package

OTOH if it is for 32 bit compilation on a 64 bit platform you *may* need g++-multilib

---

### Post by cyclingchap on 2014-08-17
Hi,

thanks for the response.

I tried installing both those packages but they didn't fix the problem....

I certainly don't think I installed either of them on 12.04 and the code compiles fine. Like I said, I don't think I installed anything w.r.t. c++ libs.

Has anything changed between 12.04 and 14.04 that causes this?

---

### Post by cyclingchap on 2014-08-18
OK,

I fixed this, so for for future reference...

A google search for "cant find lstdc++" rather than "can't find -lstdc++" found me the answer.

The -lstdc++ line in the Makefile makes the compiler look for the following library

libstdc++.so -> ../../../x86_64-linux-gnu/libstdc++.so.6 ,   which is in the /usr/lib/gcc/x86_64-linux-gnu/4.6/ folder.

For some reason this library is in my 12.04 Precise install, but not my 14.04 Trusty install.

If missing, the library is installed with:

sudo apt-get install g++-4.6-multilib

Note I'm using gfortran-4.6 and the -lstdc++ library on g++ version 4.6.4.

I'm fairly sure I didn't do the above install on 12.04 Precise, so I guess somebody changed something in the 14.04 Trusty distro.. :-)

(Note the above install is also required on Mint 16 Cinnamon)

---

### Post by steeldriver on 2014-08-18
Well the default version of g++ on Trusty is 4.8, so when you installed the g++-multlib dependency package it would have installed g++-4.8-multilib

Presumably you installed gfortran-4.6 g++-4.6 manually, which explains why you needed to install the specific g++-**4.6**-multilib package explicitly

On Precise, g++-4.6 would have been the default, so simply installing g++-multlib would have been sufficient

---


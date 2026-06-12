---
title: "What is the architecture of my petsc....."
date: 2012-11-15
forum: New to Ubuntu
---

### Post by astriedinger on 2012-11-15
What is the architecture of my petsc..... I have fe folllowing instructions given to make a file:

export PETSC_DIR=<PETSC_DIR>
export PETSC_ARCH=<ARCH>
python setup.py install



where <PETSC_DIR> is the full path of your petsc installation and <ARCH> is the architecture you used.  


But I am clear as to wha is the architecture of my petsc,,, does it mean it is 64 bit, 32 bit, etc...
HOw do I write it, and where do I find it?

KInd regards,
ALberto STriedinger PInilla

---

### Post by drmrgd on 2012-11-15
I would guess that they're referring to the architecture of the OS (although it could possibly be the architecture of the program installed if there's a choice).  You might consult any documentation you can find just to be sure; they must mention it somewhere!

To get the architecture of your OS, you can run:

```
uname -i
```

That will show you x86_64 for a 64-bit system and i386 for a 32-bit system (for example).

EDIT:  just did a quick google search and found this:

> PETSC_DIR and PETSC_ARCH are a couple of variables that control the configuration and build process of PETSc. These variables can be set as envirnment variables or specified on the command line [to both configure and make]
specify enviornment variable for csh/tcsh [can be specified in ~/.cshrc]
setenv PETSC_DIR /home/balay/petsc-3.3-p0
setenv PETSC_ARCH linux-gnu-c-debug
specify enviornment variable for bash [can be specified in ~/.bashrc]
export PETSC_DIR=/home/balay/petsc-3.3-p0
export PETSC_ARCH=linux-gnu-c-debug
specify variable on commandline to configure
./configure PETSC_DIR=/home/balay/petsc-3.3-p0 PETSC_ARCH=linux-gnu-c-debug [other configure options]
specify variables on command line to make
make PETSC_DIR=/home/balay/petsc-3.3-p0 PETSC_ARCH=linux-gnu-c-debug [other make options]
PETSC_DIR: this variable should point to the location of the PETSc installation that is used. Multiple PETSc versions can coexist on the same file-system. By changing PETSC_DIR value, one can switch between these installed versions of PETSc.

PETSC_ARCH: this variable gives a name to a configuration/build. Configure uses this value to stores the generated config makefiles in ${PETSC_DIR}/${PETSC_ARCH}/conf. And make uses this value to determine this location of these makefiles [which intern help in locating the correct include and library files].

Thus one can install multiple variants of PETSc libraries - by providing different PETSC_ARCH values to each configure build. Then one can switch between using these variants of libraries [from make] by switching the PETSC_ARCH value used.
If configure doesn't find a PETSC_ARCH value [either in env variable or command line option], it automatically generates a default value and uses it. Also - if make doesn't find a PETSC_ARCH env variable - it defaults to the value used by last successful invocation of previous configure.

Looks like you just need to enter 'linux-gnu-c-debug' in the variable, and it doesn't have anything to do with your actual system architecture.

---

### Post by astriedinger on 2012-12-11
thank you man, very much

---

### Post by astriedinger on 2012-12-11
drmrgd,

Hey I have now another issue, with an installation I did. But I dont understand what it means. THis kind of error keep appearing after I try to compile some softwares I have for my thesis:


/usr/bin/ld: /home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/lib/libpetsc.a(pinit.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/lib/libpetsc.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/s117555/sumb_2/sumb/src/python/f2py'
make: *** [LINUX_GFORTRAN_OPENMPI_PYTHON] Error 2
s117555@ubuntu:~/sumb_2/sumb$ 

It seems it is related to my petsc_arch but I have no clue how to solve it.... This is what I have in my barsch file:
export PYTHONPATH=${PYTHONPATH}:${HOME}/sumb_2/mdo_import_helper
export PETSC_DIR=/home/s117555/Downloads/petsc-3.3-p4
export PETSC_ARCH=arch-linux2-c-debug

The direction of my PETSC_DIR I Have it this way becasue when installin PETSC in the terminal it said to:

Compilers:
  C Compiler:         mpicc  -Wall -Wwrite-strings -Wno-strict-aliasing -Wno-unknown-pragmas -g3 -fno-inline -O0 
  Fortran Compiler:   mpif90  -Wall -Wno-unused-variable -Wno-unused-dummy-argument -g  
Linkers:
  Static linker:   /usr/bin/ar cr
  Dynamic linker:   /usr/bin/ar  
MPI:
  Includes: -I/usr/lib/openmpi/include -I/usr/lib/openmpi/include/openmpi
X:
  Includes: 
  Library:  -lX11
BLAS/LAPACK: -llapack -lblas
pthread:
  Library:  -lpthread
  Arch:     
PETSc:
  PETSC_ARCH: arch-linux2-c-debug
  PETSC_DIR: /home/s117555/Downloads/petsc-3.3-p4
  Clanguage: C
  Scalar type: real
  Precision: double
  Memory alignment: 16
  shared libraries: disabled
  dynamic loading: disabled
xxx=========================================================================xxx
 Configure stage complete. Now build PETSc libraries with (legacy build):
   make PETSC_DIR=/home/s117555/Downloads/petsc-3.3-p4 PETSC_ARCH=arch-linux2-c-debug all
 or (experimental with python):
   PETSC_DIR=/home/s117555/Downloads/petsc-3.3-p4 PETSC_ARCH=arch-linux2-c-debug ./config/builder.py



KInd regards,
ALberto

---


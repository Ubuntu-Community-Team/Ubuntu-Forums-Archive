---
title: "Problems with Gfortran &amp; OpenMPI"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by BenModra on 2014-06-27
Hi 

I'm trying to run a numerical model (using a work pc I have little control over, running XP) - I don't really care how, but this seemed the easiest path to take:
Install vmware player
Install the latest version of ubuntu 
Add gfortran: sudo apt-get install gfortran
Add mpi: (i forget exactly but something like sudo apt-get install mpich2 libmpich2-dev
run the make file for the model

But make spits out this:
modrab@ubuntu:~/Projects/Funwave/funwave-version2.1/src$ make
/usr/bin/cpp  -P -C -traditional  -P -C -traditional   -DPARALLEL -DSAMPLES -DCARTESIAN   -DMIXING                  mod_param.F > mod_param.f90
gfortran  -c     mod_param.f90
mod_param.f90:1.1:

/* Copyright (C) 1991-2014 Free Software Foundation, Inc.
 1
Error: Invalid character in name at (1)
mod_param.f90:2.3:

   This file is part of the GNU C Library.
   1
Error: Unclassifiable statement at (1)
mod_param.f90:4.3:

   The GNU C Library is free software; you can redistribute it and/or
   1
Error: Unclassifiable statement at (1)
mod_param.f90:4.39:

etc..

Obviously it is trying to read the comments of gfortran.

What can I do?

---

### Post by steeldriver on 2014-06-27
I don't know anything about that particular software, but if it's the version provided at [http://chinacat.coastal.udel.edu/programs/funwave/funwave.html](http://chinacat.coastal.udel.edu/programs/funwave/funwave.html) I was able to build it on 32-bit Ubuntu 12.04 using gfortran 4.6.4 and libopenmpi-dev 1.4.3 - it produces a single executable ./funwave-version2.1/work/mytvd (although I had to manually create the ../work directory) - is that what you expect? I have not tried to test it since I don't know how.

The presence of **libopenmpi-dev** seems to be important as it causes the .f90 files to be compiled with mpif90 instead of regular gfortran: 

```

$ make
/usr/bin/cpp  -P -C -traditional  -P -C -traditional   -DPARALLEL -DSAMPLES -DCARTESIAN   -DMIXING                  mod_param.F > mod_param.f90
**mpif90**  -c     mod_param.f90
/usr/bin/cpp  -P -C -traditional  -P -C -traditional   -DPARALLEL -DSAMPLES -DCARTESIAN   -DMIXING                  mod_global.F > mod_global.f90
**mpif90**  -c     mod_global.f90
.
.
.

```

so I suggest as a first shot you try installing that package and then doing a 'make clean' and 'make'

---

### Post by BenModra on 2014-06-28
Thanks for the reply.  Yes thats the software.
I've tried a fresh install of ubuntu on vmware and noted the exact steps here using your tips, I haven't done anything else since installing ubuntu:
1) >sudo apt-get install gfortran-4.6
        no errors
2) >sudo apt-get install libopenmpi-dev
        no errors
3) download and unzip the software
4) >make clean, >make

The Open MPI wrapper compiler was unable to find the specified compiler
gfortran in your PATH.

Note that this compiler was either specified at configure time or in
one of several possible environment variables.

5) >gfortran
The program 'gfortran' is currently not installed. You can install it by typing:
sudo apt-get install gfortran

6) >sudo apt-get install gfortran

7) make clean, make
/usr/bin/cpp  -P -C -traditional  -P -C -traditional   -DPARALLEL -DSAMPLES -DCARTESIAN   -DMIXING                  mod_param.F > mod_param.f90
mpif90  -c     mod_param.f90
mod_param.f90:1.1:

/* Copyright (C) 1991-2014 Free Software Foundation, Inc.
 1
Error: Invalid character in name at (1)
mod_param.f90:2.3:

   This file is part of the GNU C Library.
   1
Error: Unclassifiable statement at (1)
etc...

Am I missing something?

---

### Post by steeldriver on 2014-06-28
Hmm... well the difference seems to be in pre-processing (i.e. the behaviour of cpp is different between 12.04and 14.04), as the comments simply don't appear in the .f90 files when I look on my 12.04 box

I have since tried it in a 14.04 VM and observe the same errors as you

FWIW just installing gfortran-4.6 won't cause it to override the default (4.8), you would need to modify the /usr/bin/gfortran symlink HOWEVER I don't think that's the issue here (in fact I tried with gfortran-4.6 on 14.04 AFTER setting the symlink to make sure it really used it and got the same error).

**EDIT**: so it seems to be as simple as removing the -C option from the DEF_FLAGS Makefile variable used by cpp e.g.

```

make **"DEF_FLAGS=-P -traditional"**

```

---


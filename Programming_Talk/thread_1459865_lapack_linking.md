---
title: "lapack linking"
date: 2010-04-22
forum: Programming Talk
---

### Post by elquin on 2010-04-22
Hi, all.
I just started to use Ubuntu with the last one, 9.10.
I just installed gfortran and lapack.
This is the main reason why I choose ubuntu.
I used fortran of computing server in my university, which is based on  Intel fortran.
To make sample run with my ubuntu machine, it's little hard.
My test 'makefile' is shown as;
---------------------------------------------------
# Makefile
# Directory object:
MYDIR = /home/...

OBJS1 = ...
LIB   = -L /usr/share/man/man3/ -lmkl_lapack -lguide -lpthread
#libguide.a      libmkl_ias.so       libmkl_mc.so     libmkl_vml_def.so
#libguide.so     libmkl_lapack32.so  libmkl_p4n.so    libmkl_vml_mc.so
#libmkl_def.so   libmkl_lapack64.so  libmkl.so        libmkl_vml_p4n.so
#libmkl_em64t.a  libmkl_lapack.a     libmkl_solver.a  libvml.so

CENTRAL = ...
----------------------------------------------------

And the results are ;
---------------------------------------
gfortran -O3  -o myexe_...   -L /usr/share/man/man3/ -lmkl_lapack  -lguide -lpthread 
/usr/bin/ld: cannot find -lmkl_lapack
/usr/bin/ld: cannot find -lmkl_lapack
collect2: ld returned 1 exit status
make: *** [myexe_tmp] Error 1
------------------------------

I installed lapack from 'Synaptic Package Manager'.
Maybe it comes from the wrong LIB.
How can I fix it?

Thanks,

---

### Post by Some Penguin on 2010-04-22
"-L /usr/share/man/man3/" makes absolutely no sense at all, as it probably contains man pages, not shared libraries.  Go find wherever you put the lapack libraries and use that instead.

---

### Post by elquin on 2010-04-22
Thanks.
Sorry but i'm not good at linux command and environment.
How can I find the directory where the lapack library is stored?

---

### Post by Zugzwang on 2010-04-22
> **elquin said:**
> Thanks.
Sorry but i'm not good at linux command and environment.
How can I find the directory where the lapack library is stored?

You can look it up here: [http://packages.ubuntu.com/karmic/i386/liblapack-dev/filelist](http://packages.ubuntu.com/karmic/i386/liblapack-dev/filelist)

However, the library is called "lapack", not "mkl_lapack". How did you come up with this name?

---

### Post by elquin on 2010-04-22
Thanks.
I used that makefile in my university's computing center and they use intel fortran with lapack like that way.

I just changed the LIB in the makefile as
-----------------------------------------
LIB   = -L /usr/lib/liblapack
------------------------------------------

and after 'make' in terminal, the results are

---------------------------------------------------------------------------------------------
xxx .o: In function `__xxx_mod_MOD_ghsolver2':
xxx.f90:(.text+0x672): undefined reference to `dgesv_'
xxx.f90:(.text+0x90a): undefined reference to `dgesv_'
collect2: ld returned 1 exit status
make: *** [myexe_tmp] Error 1
---------------------------------------------------------------------------------------------

What change or option is needed on LIB in 'makefile'?

---

### Post by Zugzwang on 2010-04-22
> **elquin said:**
> 
LIB   = -L /usr/lib/liblapack


"-L" stands for an library directory, whereas "-l" denote libraries to be included (without the leading lib). Thus, you might want to use something like:
```

LIB = -llapack -lphread

```
The directory "/usr/lib" does not need to be specified as it is contained in the list of directories the linker looks into by default.

---

### Post by elquin on 2010-04-22
Sorry, but I think I miss another one.
Here I attach my sample 'makefile'

-----------------------------------------------
# Makefile
# Directory object:
MYDIR = /home/elquin/Documents/bem/utility/

OBJS1 = nrutil_mod4.o  quintic_spl.o  num_int_quad.o   data_entry.o  alloc_var_d.o  geometry_d.o  bem_ghmtx_d.o  derivs_fun.o  rk_time_integ_rk4smpl.o   central_d_rk4smpl.o  print_d.o   stag_array_d.o
LIB  = -L /usr/lib/liblapack -llapack -lphread
#libguide.a      libmkl_ias.so       libmkl_mc.so     libmkl_vml_def.so
#libguide.so     libmkl_lapack32.so  libmkl_p4n.so    libmkl_vml_mc.so
#libmkl_def.so   libmkl_lapack64.so  libmkl.so        libmkl_vml_p4n.so
#libmkl_em64t.a  libmkl_lapack.a     libmkl_solver.a  libvml.so

CENTRAL =  nrutil_mod4.o  alloc_var_d.o  data_entry.o  geometry_d.o   num_int_quad.o  rk_time_integ_rk4smpl.o  print_d.o
BEM_MTX = nrutil_mod4.o  alloc_var_d.o  num_int_quad.o
GEOM =   nrutil_mod4.o  alloc_var_d.o  num_int_quad.o   quintic_spl.o
ALLOC =  nrutil_mod4.o  num_int_quad.o
DERIVS = nrutil_mod4.o  alloc_var_d.o  data_entry.o  geometry_d.o bem_ghmtx_d.o  quintic_spl.o
MYPRINT =  nrutil_mod4.o
RKTIME = nrutil_mod4.o  alloc_var_d.o  data_entry.o derivs_fun.o print_d.o stag_array_d.o

myexe_tmp : $(OBJS1)
        gfortran -O3  -o $@  $(OBJS1)  $(LIB)
.
.
.
--------------------------------------------------------------------
and after 'make', the results are
--------------------------------------------------------------------
gfortran -O3  -c  /home/elquin/Documents/bem/utility/nrutil_mod4.f90
gfortran -O3  -c  /home/elquin/Documents/bem/utility/quintic_spl.f90
gfortran -O3  -c  /home/elquin/Documents/bem/utility/num_int_quad.f90
gfortran -O3  -c  data_entry.f90
gfortran -O3  -c  alloc_var_d.f90
gfortran -O3  -c  geometry_d.f90
gfortran -O3  -c  bem_ghmtx_d.f90
gfortran -O3  -c   derivs_fun.f90 
gfortran -O3  -c   print_d.f90 
gfortran -O3  -c   stag_array_d.f90
gfortran -O3  -c   rk_time_integ_rk4smpl.f90 
gfortran -O3  -c  central_d_rk4smpl.f90
gfortran -O3  -o myexe_tmp  nrutil_mod4.o  quintic_spl.o  num_int_quad.o   data_entry.o  alloc_var_d.o  geometry_d.o  bem_ghmtx_d.o  derivs_fun.o  rk_time_integ_rk4smpl.o   central_d_rk4smpl.o  print_d.o   stag_array_d.o  -L /usr/lib/liblapack -llapack -lphread 
/usr/bin/ld: cannot find -lphread
collect2: ld returned 1 exit status
make: *** [myexe_tmp] Error 1
------------------------------------------------------------------------------------

---

### Post by Zugzwang on 2010-04-22
Did you install the "build-essential" package?

---

### Post by elquin on 2010-04-22
What I installed is from 'Synaptic Package Manager'.
liblapack3gf
liblapack-dev
and etc.

I just followed the install process by manager.

---

### Post by Zugzwang on 2010-04-22
So go to the package manager and check that you have the "build-essential" package installed. As the name suggests, it contains stuff that you definitely need for building programs in Ubuntu.

---

### Post by elquin on 2010-04-22
I checked it but it's installed already.
build-essential 
ver.11.4

---

### Post by Zugzwang on 2010-04-22
Please verify that the following files are in place:
```

/usr/lib/libpthread.a
/usr/lib/libpthread.so

```

---

### Post by elquin on 2010-04-22
Yes, both files are shown in my system.

---


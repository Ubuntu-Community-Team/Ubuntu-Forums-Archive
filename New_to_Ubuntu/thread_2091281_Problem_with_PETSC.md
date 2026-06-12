---
title: "Problem with PETSC"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by astriedinger on 2012-12-04
Hello guys, I think I have a problem with my PETSC installation. It turns out I am compiling a code and it uses PETSC4py and in some sense PETSC with are the same but anyways...

Once I am in the folder that is to be compiled and run "make.....(aditional stuff)''  I obtain the folloing warinings at the very end:
--------------------------------------------------------------
    -I/usr/local/lib/python2.7/site-packages/numpy/f2py/src -c sumbmodule.c
sumbmodule.c: In function ‘f2py_setup_communication’:
sumbmodule.c:9398:41: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9399:41: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9401:41: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9402:41: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_inputiteration’:
sumbmodule.c:9646:42: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9658:42: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9663:42: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_inputmotion’:
sumbmodule.c:9742:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9743:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9745:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9748:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9750:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9752:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9754:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9755:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9756:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9758:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9762:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9765:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9767:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9772:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9775:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9776:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9778:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:9779:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_inputtimespectral’:
sumbmodule.c:10045:45: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10048:45: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10049:45: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_iteration’:
sumbmodule.c:10152:37: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10153:37: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10162:37: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_monitor’:
sumbmodule.c:10217:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10218:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10221:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10224:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10226:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10228:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10229:35: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_block’:
sumbmodule.c:10262:33: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_flowvarrefstate’:
sumbmodule.c:10330:43: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_costfunctions’:
sumbmodule.c:10429:41: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_adjointpetsc’:
sumbmodule.c:10470:40: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_adjointvars’:
sumbmodule.c:10532:39: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c: In function ‘f2py_setup_couplerparam’:
sumbmodule.c:10703:40: warning: assignment from incompatible pointer type [enabled by default]
sumbmodule.c:10707:40: warning: assignment from incompatible pointer type [enabled by default]
mpicc -DHAS_ISNAN     -O -fPIC    -I/usr/local/include/python2.7 -I/usr/local/include/python2.7 -I/usr/local/lib/python2.7/site-packages/numpy/core/include \
    -c /usr/local/lib/python2.7/site-packages/numpy/f2py/src/fortranobject.c -o fortranobject.o
mpif90 -I../../../mod -I../../../externals/SU_MPI/mod -I../../../externals/ADT/mod -I../../../src/inputParam -I../../../src/turbulence  -I/usr/local/include -DHAS_ISNAN  -fPIC -fdefault-real-8 -O1 -fdefault-double-8    -I/home/s117555/Downloads/petsc-3.3-p4/include -I/home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/include -I/usr/lib/openmpi/include -I/usr/lib/openmpi/include/openmpi -I/home/s117555/Downloads/petsc-3.3-p4  -I../../../mod \
    -I../../../src/python/fortran/suggar/ \
    -I../../../src/python/fortran/aeroElastic -c sumb-f2pywrappers2.f90
mpif90 -shared fortranobject.o sumbmodule.o sumb-f2pywrappers2.o  -L../../../externals/SU_MPI/lib -L../../../externals/ADT/lib -L../../../lib -lsumb  -ladt -lsu_mpi -Wl,-rpath,/usr/local/lib -lcgns  -L/home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/lib  -lpetsc -lX11 -lpthread -llapack -lblas -L/usr/lib/openmpi/lib -L/usr/lib/gcc/x86_64-linux-gnu/4.6 -L/usr/lib/x86_64-linux-gnu -L/lib/x86_64-linux-gnu -lmpi_f90 -lmpi_f77 -lgfortran -lm -lgfortran -lm -lgfortran -lm -lm -lquadmath -lm -ldl -lmpi -lopen-rte -lopen-pal -lnsl -lutil -lgcc_s -lpthread -ldl   -o sumb.so
/usr/bin/ld: /home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/lib/libpetsc.a(pinit.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/home/s117555/Downloads/petsc-3.3-p4/arch-linux2-c-debug/lib/libpetsc.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/s117555/sumb_2/sumb/src/python/f2py'
make: *** [LINUX_GFORTRAN_OPENMPI_PYTHON] Error 2
s117555@ubuntu:~/sumb_2/sumb$ 

For some reason it enters first to a python file in one of the inner directories  where I execute my comand line... and as you can see it always says INCOMPATIBLE POINTER TYPE.... 

Additionaly, the last line is trying to read something from petsc but it says the symbols have bad value (that is whay I understand from it). I am wondeirng if my petsc installation was wrong, cuz at the begining I could get around it.

I was given this advice:

"  The easiest way to do it is to download petsc4py from the website.  Untar it. In the petsc4py folder create a file called setup.sh with the  following contents:
 

export PETSC_DIR=<PETSC_DIR>
export PETSC_ARCH=<ARCH>
python setup.py install



where <PETSC_DIR> is the full path of your petsc installation and <ARCH> is the architecture you used.  Then run:
 

sudo sh ./setup.sh


which should install it properly for you. 


To test that it worked properly run:


python -c 'from petsc4py import PETSc'
              "

From a teacher in U.S 

CAN ANYBODY PLEASE let me know how to procede with this problem?? I need this code for my thesis, and pretty much cannot do anything if it aint running =/

---


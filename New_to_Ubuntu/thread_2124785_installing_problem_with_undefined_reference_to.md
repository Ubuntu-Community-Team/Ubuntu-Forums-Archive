---
title: "installing problem with undefined reference to"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by clarklipman on 2013-03-12
Dear All, 

I am tring to install a numerical code program. When I give the sh command, at the end of make, come out this error:
make[3]: Entering directory `/home/user/bob/titan-2.0.1/src/main'
/usr/local/bin/mpicxx -I../gisapi/ -g -O2 -w -g -O2 -DMPICH_IGNORE_CXX_SEEK  -I/usr/include -D__HAVE_HDF5__  -L/usr/lib -o titan titan-compare_key.o titan-delete_tab.o titan-hpfem.o titan-datread.o titan-hilbert.o titan-init_piles.o titan-update_topo.o titan-restart.o ../gisapi/libgisapi.a ../adapt/libadapt.a  -L/usr/lib/gcc/i686-linux-gnu/4.6 -L/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu -L/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib -L/lib/i386-linux-gnu -L/lib/../lib -L/usr/lib/i386-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/i686-linux-gnu/4.6/../../.. -lgfortran -lm -lquadmath ../datstr/libdatstr.a ../geoflow/libgeoflow.a ../useful/libuseful.a ../repartition/librepartition.a ../tecplot/libtecplot.a -lnsl -lz -lm -lhdf5 -lmpich -lpthread 
../datstr/libdatstr.a(element2.o): In function `Element::correct(HashTable*, HashTable*, double, MatProps*, FluxProps*, TimeProps*, double*, double*, double*, double*)':
/home/user/bob/titan-2.0.1/src/datstr/element2.C:2463: undefined reference to `correct_'
../geoflow/libgeoflow.a(Correct.o): In function `correct(HashTable*, HashTable*, double, MatProps*, FluxProps*, TimeProps*, void*, double*, double*, double*, double*)':
/home/user/bob/titan-2.0.1/src/geoflow/Correct.C:107: undefined reference to `correct_'
collect2: ld returned 1 exit status
make[3]: *** [titan] Error 1
make[3]: Leaving directory `/home/user/bob/titan-2.0.1/src/main'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/user/bob/titan-2.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/bob/titan-2.0.1'
make: *** [all] Error 2

I have looked in the source code of both element2.C and Correct.C files, they have listed the Correct_ function. Do I have a problem with gcc library version install on my Xubuntu (I have a gcc-4.6.3-1ubuntu5 version). Do I need an older one? is it a problem of link libraries. I am very new to linux and I need someone help.

---

### Post by schragge on 2013-03-17
This definitely looks like a linking problem. Did you follow the installation procedure outlined in [http://www.gmfg.buffalo.edu/software/titan_userguide.pdf](http://www.gmfg.buffalo.edu/software/titan_userguide.pdf) (3.2.1 Compiling the Code)? Particularly, this step
```
configure --with-mpi=<mpi main directory> --with-hdf5=<hdf5 directory>
```

---


---
title: "Trying to compile old program with G77 compiler"
date: 2014-10-06
forum: Programming Talk
---

### Post by Chris_Laskaris on 2014-10-06
Hello everyone.

I am trying to use a vegetation modelling program named BIOME 4, available for download here:
[https://pmip2.lsce.ipsl.fr/synth/biome4.shtml](https://pmip2.lsce.ipsl.fr/synth/biome4.shtml)

It is an old program and supposed to be compiled with the now outdated GNU g77 compiler. I tried using newer compilers like gfortran and fort77 instead, but they do not compile the code correctly when using make (I get a myriad of "undefined reference" errors.

So I found a g77 compiler here and installed it:
[http://gnxas.unicam.it/XASLABwww/pag_gnxas/gnxas_install_g77lib.html](http://gnxas.unicam.it/XASLABwww/pag_gnxas/gnxas_install_g77lib.html)

However, even trying to compile with g77 produces various "undefined reference" errors, so maybe that was not the right kind of package.

Does anyone know of an alternative Fortran 77 compiler that might work with this program on Ubuntu 12.0.4? As I wrote, gfortran and fort77 did not work, but maybe there are other compilers I could try. Or, as another possible solution, does anyone know where to get an old GNU g77 package that works?

Thank you for your help.

---

### Post by steeldriver on 2014-10-06
Well - I was able to build it on my 32-bit 12.04 box using gfortran as follows

1. the first thing to note is that the tarball includes old object code (.o files) - if you try to make without clearing those out then it will go straight to the link phase and try to link against (almost certainly) incompatible system libraries. So you will need to either manually remove these or

```

make clean

```

first.

2. you will need the libnetcdf-dev package installed. You *could* download and build the latest netcdf C and Fortran libraries from [http://www.unidata.ucar.edu/downloads/netcdf/index.jsp](http://www.unidata.ucar.edu/downloads/netcdf/index.jsp) (I did initially, assuming that was the issue - before figuring out it probably wasn't), however it seems to build fine with the version from the repository which you can install either via Software Center or

```

sudo apt-get install libnetcdf-dev

```

3. the Fortran netcdf library has been split from the C library so you need to add that to the Makefile (also if you're using the system libnetcdf instead of one installed in opt, you need to modify the include and lib paths)

```

NETCDFINCDIR = **/usr/include**
NETCDFLIB    = **-lnetcdff** -lnetcdf
NETCDFLIBDIR = **/usr/lib**

```

You also need to remove the -fno-silent flag, which gfortran doesn't appear to support

```

#FFLAGS = $(OTHERFLAGS) **-fno-silent** -Wall $(INCDIRS)
FFLAGS = $(OTHERFLAGS) -Wall $(INCDIRS)

```

4. there appears to be only one actual compile error, related to a WRITE format

```

biome4.f:250.31:

       write(*,'(A,2F7.2,3F7.1,)')                                      
                               1
Error: Unexpected element ')' in format string at (1)

```

which *appears* to be fixable just by deleting the trailing comma

```

       write(*,'(A,2F7.2,3F7.1)')

```

Since I don't really speak Fortran, I don't know whether that is an acceptable solution, however

```

make "FC=gfortran"

```

then runs without error (although plenty of warnings) and produces a biome4 binary which at least loads and runs

```

$ ./biome4 
 reading attributes file
 opening input file
 No such file or directory     

```

Hope this helps.

---

### Post by Chris_Laskaris on 2014-10-07
Awesome! Thank you very much for your help and your detailed reply.

I got it to compile with gfortran by following your instructions. The compiled program runs fine and produces meaningful data (to actually run it, one has to specify the path to the input and output data in the biome4options file - otherwise, you get the " No such file or directory" error mentioned above).

---


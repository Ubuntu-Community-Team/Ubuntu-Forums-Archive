---
title: "Error compiling gcc 4.4.1"
date: 2009-10-03
forum: Packaging and Compiling Programs
---

### Post by invisiblecousin on 2009-10-03
Hello,

I am trying to compile GCC 4.4.1. I downloaded the core package and the package for the c++ language(gcc-g++-4.4.1.tar.bz2). I then unpacked first the core package and then the second one in the same directory. The ./configure command was run with the CFLAGS=-m64 parameter.

When I issued the make command this is what I get at some point:

/usr/local/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/local/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/local/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/local/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/local/x86_64-unknown-linux-gnu/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make[5]: *** [libgcc_s.so] Error 1
make[5]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/32/libgcc'
make[4]: *** [multi-do] Error 1
make[4]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/libgcc'
make[3]: *** [all-multi] Error 2
make[3]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/libgcc'
make[2]: *** [all-stage1-target-libgcc] Error 2
make[2]: Leaving directory `/media/Data/Work/gcc-4.4.1'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/media/Data/Work/gcc-4.4.1'
make: *** [all] Error 2

I am running Ubuntu 9.04 x64 and I also installed binutils from GNU..

---

### Post by MadCow108 on 2009-10-03
your libc is incompatible
maybe the version is wrong or it has been compiled for 32 bit

---

### Post by dinxter on 2009-10-03
if your on i386 compiling for 64 bit you'll need the libc6 64 bit libraries from the repository (libc6-amd64 i think its called)
on a side note, i believe passing CFLAGS=-m64 isnt recommended, something to do with overriding optimisations, you can pass CFLAGS="-m64 -g -02" instead but generally its better to use CC="gcc -m64" and not use CFLAGS

---

### Post by falconindy on 2009-10-04
You may want to check your current build of gcc for a full complement of flags used to configure. Omitting one may lead to undesirable or unexpected behaviors.
```
gcc -v
```

---

### Post by invisiblecousin on 2009-10-05
Well, Synaptic shows me that I have libc6 and libc6-dev (version 2.9-4ubuntu6.1) installed. I notice that there aren't any libc6-amd64 libraries so I think these two are for 64 bit because I see another package called libc6-i386..

I tried compiling it without the -m64 option in the CFLAGS, but I used instead CC=gcc -m64 and the following error occured:

In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from ../../.././libgcc/../gcc/tsystem.h:87,
                 from ../../.././libgcc/../gcc/libgcc2.c:29:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make[5]: *** [_muldi3.o] Error 1
make[5]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/32/libgcc'
make[4]: *** [multi-do] Error 1
make[4]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/libgcc'
make[3]: *** [all-multi] Error 2
make[3]: Leaving directory `/media/Data/Work/gcc-4.4.1/x86_64-unknown-linux-gnu/libgcc'
make[2]: *** [all-stage1-target-libgcc] Error 2
make[2]: Leaving directory `/media/Data/Work/gcc-4.4.1'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/media/Data/Work/gcc-4.4.1'
make: *** [all] Error 2

This is what I get when I run gcc -v command:

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)

---

### Post by dinxter on 2009-10-05
The stubs-32.h error is caused by missing i386 dev libraries
$sudo apt-get install libc6-dev-i386

---

### Post by invisiblecousin on 2009-10-06
Gee thanks! This did the trick :)

---


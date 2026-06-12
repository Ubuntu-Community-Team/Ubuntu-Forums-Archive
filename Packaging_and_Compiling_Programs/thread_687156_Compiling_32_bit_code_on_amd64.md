---
title: "Compiling 32 bit code on amd64"
date: 2008-02-04
forum: Packaging and Compiling Programs
---

### Post by theharshone on 2008-02-04
Hi
I'm trying to compile drivers for my printer (IP1800), but canon only provides rpms for 32 bit. They also provided a src.rpm, and i was able to get the sources. They also included a lot of libraries without the source and only in 32-bit. So far, i cannot get the program to compile against my 32 bit libraries in /lib32 and /usr/lib32. It insists on linking with the 64 bit version even when i set the LDFLAGS to compile to /lib32 and /usr/lib32. Here is my error...

./configure  CC=gcc-4.2 -m32 LDFLAGS=-L/lib32 -L/usr/lib32 -L/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32


make  all-recursive
make[1]: Entering directory `/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter'
Making all in src
make[2]: Entering directory `/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter/src'
gcc-4.2 -m32  -O2 -L../../292/libs_bin -L/lib32 -L/usr/lib32 -L/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32 -o cif bjferror.o bjfilter.o bjfimage.o bjfoption.o bjfpos.o bjfrcaccess.o getipc.o bjflist.o -lcnbpcmcm292 -lcnbpess292 -lm -ldl -ltiff -lpng -lcnbpcnclapi292 -lcnbpcnclbjcmd292 -lcnbpcnclui292 -lpopt
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.1/../../../libtiff.so when searching for -ltiff
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.1/../../../libtiff.a when searching for -ltiff
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libtiff.so when searching for -ltiff
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libtiff.a when searching for -ltiff
/usr/bin/ld: skipping incompatible /usr/lib/libtiff.so when searching for -ltiff
/usr/bin/ld: skipping incompatible /usr/lib/libtiff.a when searching for -ltiff
/usr/bin/ld: cannot find -ltiff
collect2: ld returned 1 exit status
make[2]: *** [cif] Error 1
make[2]: Leaving directory `/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/rpm/BUILD/cnijfilter-common-2.70/cnijfilter'
make: *** [all] Error 2

I cannot get it to compile aginst the 32 bit version. Any help is appreciated.

ps. Sorry its sorta confusing...:(

---

### Post by plugwash on 2008-02-04
do you have gcc-multilib installed?

---

### Post by theharshone on 2008-02-05
I do. I just can't get make to link to the 32 bit library. I really would like to compile this so i can get my printer to work.

---

### Post by plugwash on 2008-02-06
I think you need to symlink libtiff.so to libtiff.so.4 in /usr/lib32 , normally the -dev package does this but there is no -dev package for the 32 bit libtiff.

---

### Post by theharshone on 2008-02-08
it is already linked to libtiff.so.4.
Is there a way to manually edit the make file and change this?

---

### Post by devendra.vyavahare on 2009-02-03
> **plugwash said:**
> do you have gcc-multilib installed?

Thanks.
This fixed my problem for compiling openimpact on 64-bit ubuntu.

---


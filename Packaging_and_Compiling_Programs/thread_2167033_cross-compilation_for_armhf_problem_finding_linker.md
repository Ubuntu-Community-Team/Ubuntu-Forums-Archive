---
title: "cross-compilation for armhf: problem finding linker library"
date: 2013-08-12
forum: Packaging and Compiling Programs
---

### Post by hvn2 on 2013-08-12
Hi,

I'm trying to cross-compile for armhf and have a linker problem. First try is using Eclipse, and while all settings are as supposed to be, it reports that it can't find the linker library. Second try is using commandline: 
'/usr/bin/arm-linux-gnueabihf-g++ test.cpp -o test -I/usr/arm-linux-gnueabihf/include/c++/4.6.3/arm-linux-gnueabihf -l/usr/lib/gcc/arm-linux-gnueabihf/4.6/'. 
However, this goes the same way: 
'/usr/lib/gcc/arm-linux-gnueabihf/4.6/../../../../arm-linux-gnueabihf/bin/ld: cannot find -l/usr/lib/gcc/arm-linux-gnueabihf/4.6/
collect2: ld returned 1 exit status
The directory obviously exists: 
ls /usr/lib/gcc/arm-linux-gnueabihf/4.6
4.6/   4.6.3/ 

So my question is: where does it go wrong? Is this linker library indeed the library or not? As far as I know the full toolchain is installed.

Thanks

---

### Post by hvn2 on 2013-08-12
Problem is solved by adjusting settings.

---


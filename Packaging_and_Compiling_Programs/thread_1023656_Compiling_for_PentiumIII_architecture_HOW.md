---
title: "Compiling for PentiumIII architecture: HOW?"
date: 2008-12-28
forum: Packaging and Compiling Programs
---

### Post by finzic on 2008-12-28
Hello to you all, this is my 1st post in Ubuntu Forums!
Straight to the point.
My box is a Celeron Coppermine (PentiumIII).
I found that the stock kernel 2.6.27-generic is built for a very generic target arch, so I wanted to build my own to get some speed.
I found that the installed gcc reports as follows: 
-----------------
finzic@ubuntu:/usr/src/linux$ gcc -v
Using built-in specs.
Target: **i486-linux-gnu**
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=**i486-linux-gnu** --host=**i486-linux-gnu** --target=**i486-linux-gnu**
-----------------

Reason for setting gcc properly is that I wanted also to build RUBY from sources because the stock one was apparently built for the i486 arch, and I want my Linux to squeeze every bit out of my Celeron (why having a different CPU if you don't use it?)

so here are my questions: 
1) why is GCC apparently set to compile for a 486 arch? How to set it to actually create code for pentium III (-march=pentium3 should be the correct option... or am I wrong?)

2) what are the official Ubuntu 8.10 rules to re-build a kernel? I followed these ones: 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Thanks in advance, 
Luca.

---


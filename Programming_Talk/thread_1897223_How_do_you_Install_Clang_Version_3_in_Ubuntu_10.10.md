---
title: "How do you Install Clang Version 3 in Ubuntu 10.10?"
date: 2011-12-18
forum: Programming Talk
---

### Post by haziz on 2011-12-18
How would I go  about installing version 3 of Clang/LLVM in Ubuntu 10.10? Ubuntu 10.10  installs version 2.8 by default. Version 3 has more extensive/up to date  support for C++ and possibly C (I am not totally sure about C). I know  that I could possibly compile from source but was wondering if there is a  ppa or other method to avoid compiling it from source.
 
If I compile from source do I have to tell it where to find the std c library etc. or is that automatically done.

Thanks.

---

### Post by jake.anq on 2011-12-18
Hi

The website [here]("http://clang.llvm.org/get_started.html") has instructions of how to install Clang. from source.  There does not appear to be packages for 10.10

All of the necessary files should be found by the ./configure script.

If there are any errors, it will probably be due to packages that you need to install.

---

### Post by MadCow108 on 2011-12-19
12.04 has llvm3 you might be able to install the packages from there in 10.10
if not you can try backportpackage from ubuntu-dev-tools (which also might fail due to packaging tool changes).

or install 12.04 in a VM/chroot.

---

### Post by buse385 on 2012-02-26
I installed clang 3.0 on ubuntu 11.10 64 bit. But the instructions won't change. Just visit here:
[http://lifesnotsimple.com/index.php/2011/12/compiling-clang-on-ubuntu-11-10/](http://lifesnotsimple.com/index.php/2011/12/compiling-clang-on-ubuntu-11-10/)

---


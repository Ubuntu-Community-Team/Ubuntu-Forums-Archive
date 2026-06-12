---
title: "powerpc-linux-gnu cross toolchain"
date: 2009-08-19
forum: Packaging and Compiling Programs
---

### Post by caldo_de_cana on 2009-08-19
Hi,

I have an x86_64 running ubuntu server 9.04. I also have a powerpc running ubuntu server 9.04. I am trying to build a cross-compiler in the x86_64 machine that will target the powerpc.

I got to build binutils with apt-get source, dpkg-source -x, and TARGET=<...> fakeroot debian/rules. But I don't know how to proceed after that. I suppose I would have to cross build a simple gcc (using GCC_TARGET failed at the first use of xgcc), then build glibc, and after that re-build gcc.

Are there any clean and simple instructions to build such a cross-compiler?

Ramiro Polla

---


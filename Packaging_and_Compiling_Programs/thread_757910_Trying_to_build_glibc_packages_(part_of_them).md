---
title: "Trying to build glibc packages (part of them)"
date: 2008-04-17
forum: Packaging and Compiling Programs
---

### Post by evcosta on 2008-04-17
I am trying to build glibc 2.5 (Feisty) packages from apt-getted sources. I found it builds every possible library by default. For example I do not want profile, debug, udeb. One of the build logs (log-test-i486-linux-gnu-libc) is showing an error that AFAICT is related to the profile libraries build (seen at a Redhat forum old message). Also I do not want to spend time building the amd64 and xen libraries. 

I deleted some entries from debian/control but it did not work. I tried to find information in man pages as well as the internet with no success. Where can I control what is built?

Any suggestion or pointer is welcome.

Thank you very much in advance.

Elder.

---

### Post by geraldm on 2008-04-17
You need to find what parameters to pass to the configure program.
Usually in the top source directory 
```

./configure --help

```
This should return the main parameters. 

There is a useful project at [http://www.linuxfromscratch.org](http://www.linuxfromscratch.org) for their LFS project.  There is an online book in which you can find glibc  -- they build it in chapter 5 and again in chapter 6.  Their project tailors the configure for their build (which you would not want to use exactly) but it does discuss each parameter.  Here is a quick look for their glibc-2.5.1
../glibc-2.5.1/configure --prefix=/tools \
    --disable-profile --enable-add-ons \
    --enable-kernel=2.6.0 --with-binutils=/tools/bin \
    --without-gd --with-headers=/tools/include \
    --without-selinux

Gerald

---

### Post by evcosta on 2008-04-18
Is there a way to do it through dpkg-buildpackage or other tool? If not, after configuring and compiling, how do I build the deb package?

Edited: actually, is there a way to select one step that dpkg-buildpackage execute at a time? To do such a configure I should have it patch the pristine tree, ./configure to customize it and then to compile and package.

Thanks.

Elder.

---


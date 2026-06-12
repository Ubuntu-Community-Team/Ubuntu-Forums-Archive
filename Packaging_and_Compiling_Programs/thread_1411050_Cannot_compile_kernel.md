---
title: "Cannot compile kernel"
date: 2010-02-19
forum: Packaging and Compiling Programs
---

### Post by manoriax on 2010-02-19
Hey,
recently I've tried to compile a custom kernel, but somehow it failed to compile every time I tried. That's what I've done:
```
mkdir src
```to create a directory to work in. Then I changed into that directory by typing
```
cd src
```Then I executed
```
apt-get source linux-image-$(uname -r)
```to get the latest kernel  sources. Then I copied my current (working) kernel configuration by typing
```
cp -vi /boot/config-`uname -r` .config
```and did
```
make menuconfig
```after that to check whether my settings are still okay.
I replaced one of the source files by a file modified by me (the reason for my attempts of compiling the kernel) and did
```
export CONCURRENCY_LEVEL=3
``````
make-kpkg clean
```and
```
fakeroot make-kpkg --initrd --append-to-version=-webcamtest kernel-image kernel-headers
```It started compiling the files and exited the process with
```
 LD [M]  net/x25/x25.o
make[1]: Leaving directory  `/home/phil/src/linux-2.6.32'make:  *** [debian/stamp/build/kernel] Error 2


```So, urm - did I do anything wrong? I'm currently using Ubuntu 10.04 for some tests.

Thanks in advance.

Regards

---

### Post by manoriax on 2010-02-21
Problem solves - the gspca driver had the wrong version, so it stopped compiling at this point.

---


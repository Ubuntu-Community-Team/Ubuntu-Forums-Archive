---
title: "precompiled crosstool-ng toolchain failed on ubuntu server 12.04"
date: 2012-12-01
forum: Packaging and Compiling Programs
---

### Post by gorgone on 2012-12-01
hi
i have a strange problem with precompiled crosstoolchains
i use it to build my bins for fritzbox

on debian wheezy
```
root@BIGNAS:/opt/simplebuild/toolchains/fritz33xx/bin# ./mips-linux-uclibc-gcc --version
mips-linux-uclibc-gcc (GCC) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
on ubuntu server 12.04
```
root@SIMTESTUBUNTUSERVER:/opt/simplebuild/toolchains/fritz33xx/bin# ./mips-linux-uclibc-gcc --version
bash: ./mips-linux-uclibc-gcc: No such file or directory
```

i dont known why its work on debian but not on ubuntu both 64bit

i installed this packages for my environment
```
ia32-libs ia32-libs-dev  libc6-dev zlib1g-dev lib32z1-dev lib32bz2-dev dialog xz-utils gawk subversion gcc make libusb-dev libusb-1.0-0 libusb-1.0-0-dev libssl-dev libpcsclite-dev libccid libc6-dev zlib1g-dev build-essential module-assistant
```

Toolchain link [http://www.multiupload.nl/XGLU2TZ4YR]("http://www.multiupload.nl/XGLU2TZ4YR")

thanks

---

### Post by gorgone on 2012-12-02
solution found```
apt-get install gcc-multilib
```

---


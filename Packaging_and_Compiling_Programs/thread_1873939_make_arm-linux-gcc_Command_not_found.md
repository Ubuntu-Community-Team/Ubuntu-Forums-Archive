---
title: "make: arm-linux-gcc: Command not found"
date: 2011-11-02
forum: Packaging and Compiling Programs
---

### Post by renjitha on 2011-11-02
hi,
i am working on Ubuntu 8.04...
i am trying to build a kernel for an ARM board... i am not able to create the uImage...

it gives error as below:

root@esds-desktop:~/vanilla-linux/linux-2.6.25# make ARCH=arm  CROSS_COMPILE=arm-linux- uImage
make: arm-linux-gcc: Command not found
  CHK     include/linux/version.h
make[1]: `include/asm-arm/mach-types.h' is up to date.
  CHK     include/linux/utsrelease.h
  CC      arch/arm/kernel/asm-offsets.s
/bin/sh: arm-linux-gcc: not found
make[1]: *** [arch/arm/kernel/asm-offsets.s] Error 127
make: *** [prepare0] Error 2


Can some one suggest a solution....is it because the gcc is not being identified??
And what are these error 127 and error 2..??

Regards.

---


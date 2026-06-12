---
title: "binutils-2.18 fails compiling for arm-elf"
date: 2008-11-09
forum: Packaging and Compiling Programs
---

### Post by punischdude on 2008-11-09
Hey guys,

in order to get an arm-elf toolchain I tried to compile binutils-2.18 for arm-elf (w/ and w/o the installer script from [http://forum.mcuprogramming.com/arm/gnu-arm-toolchain-installer](http://forum.mcuprogramming.com/arm/gnu-arm-toolchain-installer) ) using Intrepid.

Make always fails with following error:
```
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd -I. -I. -I/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd -I/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/../include -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Werror -g -O2 -c /home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/elf32-arm.c -o elf32-arm.o
cc1: warnings being treated as errors
/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/elf32-arm.c: In function 'find_thumb_glue':
/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/elf32-arm.c:2524: error: ignoring return value of 'asprintf', declared with attribute warn_unused_result
/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/elf32-arm.c: In function 'find_arm_glue':
/home/tobias/Desktop/gnu-arm-installer/src/binutils-2.18/bfd/elf32-arm.c:2557: error: ignoring return value of 'asprintf', declared with attribute warn_unused_result
make[4]: *** [elf32-arm.lo] Fehler 1
make[4]: Verlasse Verzeichnis '/home/tobias/Desktop/gnu-arm-installer/build/binutils-2.18/bfd'
make[3]: *** [all-recursive] Fehler 1
make[3]: Verlasse Verzeichnis '/home/tobias/Desktop/gnu-arm-installer/build/binutils-2.18/bfd'
make[2]: *** [all] Fehler 2
make[2]: Verlasse Verzeichnis '/home/tobias/Desktop/gnu-arm-installer/build/binutils-2.18/bfd'
make[1]: *** [all-bfd] Fehler 2
make[1]: Verlasse Verzeichnis '/home/tobias/Desktop/gnu-arm-installer/build/binutils-2.18'
make: *** [all] Fehler 2

```

Any idea how to fix this?

---


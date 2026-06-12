---
title: "Cross Compiling for mips target on X86 host"
date: 2010-05-04
forum: Packaging and Compiling Programs
---

### Post by Vinny_P on 2010-05-04
Hi all,

I'm trying to compile gcc for mips on my X86 machine. I have followed the instruction found: [http://www.ifp.illinois.edu/~nakazato/tips/xgcc.html](http://www.ifp.illinois.edu/~nakazato/tips/xgcc.html) with binutils-2.18, gcc-4.4.1 and newlib-1.18.0. But I get the following error message:

mips-elf-gcc -B/home/vinny/mips-build/build-newlib/mips-elf/newlib/ -isystem /home/vinny/mips-build/build-newlib/mips-elf/newlib/targ-include -isystem /home/vinny/mips-build/newlib-1.18.0/newlib/libc/include -B/home/vinny/mips-build/build-newlib/mips-elf/libgloss/mips -L/home/vinny/mips-build/build-newlib/mips-elf/libgloss/libnosys -L/home/vinny/mips-build/newlib-1.18.0/libgloss/mips    -DPACKAGE_NAME=\"newlib\" -DPACKAGE_TARNAME=\"newlib\" -DPACKAGE_VERSION=\"1.18.0\" -DPACKAGE_STRING=\"newlib\ 1.18.0\" -DPACKAGE_BUGREPORT=\"\" -I. -I../../../../../newlib-1.18.0/newlib/libc/argz -DMISSING_SYSCALL_NAMES -fno-builtin      -g -O2 -c -o lib_a-dummy.o `test -f 'dummy.c' || echo '../../../../../newlib-1.18.0/newlib/libc/argz/'`dummy.c
**as: unrecognized option '-EB'**
make[4]: *** [lib_a-dummy.o] Error 1

Can someone please help. :-)

Thank you,
Vinny

---

### Post by Vinny_P on 2010-05-04
Hi,

A colleague of mine referred me to a cross compiler tool: [http://freshmeat.net/projects/crosstool-ng/](http://freshmeat.net/projects/crosstool-ng/).

Hope this helps someone :-),
Vinny P

---


---
title: "-maltivec error?"
date: 2007-03-28
forum: Programming Talk
---

### Post by k0mpresd on 2007-03-28
cross-post from another forum since i didnt receive any responses

anyways..i am trying to cross-compile the 2.6.20 kernel to boot on the xbox360 but i received some errors

i have made it this far w/ help from you guys...more help please?

> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ export PATH=$PATH://home/k0mpresd/crosstool-0.43/build/powerpc64-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.6/gcc-core-prefix/bin
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/opt/crosstool/gcc-4.1.0-glibc-2.3.6/powerpc64-unknown-linux-gnu/bin:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CC      arch/powerpc/kernel/asm-offsets.s
  GEN     include/asm-powerpc/asm-offsets.h
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/pnmtologo
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/bin2c
  CC      init/main.o
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  CC      init/do_mounts.o
  CC      init/do_mounts_rd.o
  CC      init/do_mounts_initrd.o
  LD      init/mounts.o
  CC      init/initramfs.o
  CC      init/calibrate.o
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  GEN     usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/powerpc/kernel/semaphore.o
  CC      arch/powerpc/kernel/cputable.o
  CC      arch/powerpc/kernel/ptrace.o
  CC      arch/powerpc/kernel/syscalls.o
  CC      arch/powerpc/kernel/irq.o
  CC      arch/powerpc/kernel/align.o
  CC      arch/powerpc/kernel/signal_32.o
  CC      arch/powerpc/kernel/pmc.o
  CC      arch/powerpc/kernel/vdso.o
  CC      arch/powerpc/kernel/init_task.o
  CC      arch/powerpc/kernel/process.o
  AS      arch/powerpc/kernel/systbl.o
  CC      arch/powerpc/kernel/idle.o
  LDS     arch/powerpc/kernel/vdso32/vdso32.lds
  VDSO32A arch/powerpc/kernel/vdso32/sigtramp.o
as: unrecognized option `-maltivec'
make[2]: *** [arch/powerpc/kernel/vdso32/sigtramp.o] Error 1
make[1]: *** [arch/powerpc/kernel/vdso32] Error 2
make: *** [arch/powerpc/kernel] Error 2

---

### Post by lloyd_b on 2007-03-28
Run the following in a terminal window:
```
as --version
```

What I suspect you'll find is that the version of "as" installed on your machine can only handle x86 processors.

Try installing the package "binutils-multiarch", and see if that resolves the issue.

Lloyd B.

---

### Post by k0mpresd on 2007-03-28
k0mpresd@k0mp:~$ as --version
GNU assembler 2.17
Copyright 2005 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License.  This program has absolutely no warranty.
This assembler was configured for a target of `i686-pc-linux-gnu'.

---

### Post by k0mpresd on 2007-03-28
i downloaded "binutils-multiarch_2.17-3_i386"

it says:
> Package: binutils-multiarch
Status: Error: Dependency is not satisfiable: binutils

---

### Post by k0mpresd on 2007-03-28
i was told the kernel does not compile correctly w/ gcc-4.1.0, gcc-4.1.1 must be used

---


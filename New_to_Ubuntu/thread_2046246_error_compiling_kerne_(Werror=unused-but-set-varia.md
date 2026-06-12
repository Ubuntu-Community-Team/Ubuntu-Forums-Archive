---
title: "error compiling kerne (Werror=unused-but-set-variable)"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by amin021023 on 2012-08-22
hi all Im not sure this is the right place,plz tell me if it's wrong.

I was trying to compile a kernel for my android phone then I got this:

```
scripts/kconfig/conf -s arch/arm/Kconfig
  CHK     include/linux/version.h
  SYMLINK include/asm -> include/asm-arm
make[1]: `include/asm-arm/mach-types.h' is up to date.
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
scripts/mod/modpost.c: In function ‘get_markers’:
scripts/mod/modpost.c:1542:12: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result [-Wunused-result]
scripts/mod/modpost.c: In function ‘add_marker’:
scripts/mod/modpost.c:1962:10: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result [-Wunused-result]
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  CC      kernel/bounds.s
  GEN     include/linux/bounds.h
  CC      arch/arm/kernel/asm-offsets.s
  GEN     include/asm/asm-offsets.h
  CALL    scripts/checksyscalls.sh
  CC      init/main.o
  HOSTCC  usr/gen_init_cpio
  GEN     usr/initramfs_data.cpio.gz
In file included from include/linux/mempolicy.h:62:0,
                 from init/main.c:51:
include/linux/pagemap.h: In function 'fault_in_pages_readable':
include/linux/pagemap.h:416:16: error: variable 'c' set but not used [-Werror=unused-but-set-variable]
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
cc1: all warnings being treated as errors

make[1]: *** [init/main.o] Error 1
make: *** [init] Error 2
make: *** Waiting for unfinished jobs....
```

what if I just remove/disable werror options from compiler,is that a good idea?so how to do that?

could you help me remove werror options?this is the toolchain I use:
[https://github.com/DooMLoRD/android_prebuilt_toolchains](https://github.com/DooMLoRD/android_prebuilt_toolchains)

---


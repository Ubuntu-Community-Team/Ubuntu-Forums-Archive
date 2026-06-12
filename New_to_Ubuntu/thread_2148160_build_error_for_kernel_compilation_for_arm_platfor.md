---
title: "build error for kernel compilation for arm platform"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by rameshandroid on 2013-05-24
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi-
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: `include/generated/mach-types.h' is up to date.
  CALL    scripts/checksyscalls.sh
  CHK     include/generated/compile.h
fatal: No names found, cannot describe anything.
  CC      arch/arm/mm/init.o
In file included from arch/arm/mm/init.c:27:0:
/home/a/fresh/linux-2.6.36/arch/arm/include/asm/tlb.h: In function ‘tlb_flush_mmu’:
/home/a/fresh/linux-2.6.36/arch/arm/include/asm/tlb.h:101:3: error: implicit declaration of function ‘release_pages’ [-Werror=implicit-function-declaration]
/home/a/fresh/linux-2.6.36/arch/arm/include/asm/tlb.h: In function ‘tlb_remove_page’:
/home/a/fresh/linux-2.6.36/arch/arm/include/asm/tlb.h:164:3: error: implicit declaration of function ‘page_cache_release’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[1]: *** [arch/arm/mm/init.o] Error 1

---

### Post by dino99 on 2013-05-24
you still can use the compiled ones
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/)

---


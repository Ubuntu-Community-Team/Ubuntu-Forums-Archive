---
title: "make error compiling glibc 2.6.1"
date: 2007-08-21
forum: Programming Talk
---

### Post by 50cc on 2007-08-21
I am compiling GlibC 2.6.1 using an updated Feisty Fawn box. I ran ./configure successfully, but when I run make I get this:

```

BLA BLA BLA.....

gcc   -nostdlib -nostartfiles -shared -o /usr/src/glibc-2.6.1_build/elf/ld.so                   \
                  -Wl,-z,combreloc -Wl,-z,relro -Wl,--hash-style=both -Wl,-z,defs       \
                  /usr/src/glibc-2.6.1_build/elf/librtld.os -Wl,--version-script=/usr/src/glibc-2.6.1_build/ld.map              \
                  -Wl,-soname=ld-linux.so.2 -T /usr/src/glibc-2.6.1_build/elf/ld.so.lds
/usr/src/glibc-2.6.1_build/elf/librtld.os: In function `print_statistics':
/usr/src/glibc-2.6.1/elf/rtld.c:2800: undefined reference to `__stack_chk_fail_local'
/usr/src/glibc-2.6.1_build/elf/librtld.os: In function `process_dl_debug':
/usr/src/glibc-2.6.1/elf/rtld.c:2436: undefined reference to `__stack_chk_fail_local'
/usr/src/glibc-2.6.1_build/elf/librtld.os: In function `process_envvars':
/usr/src/glibc-2.6.1/elf/rtld.c:2695: undefined reference to `__stack_chk_fail_local'
/usr/src/glibc-2.6.1_build/elf/librtld.os: In function `dl_main':
/usr/src/glibc-2.6.1/elf/rtld.c:2316: undefined reference to `__stack_chk_fail_local'
/usr/src/glibc-2.6.1_build/elf/librtld.os: In function `print_search_path':
/usr/src/glibc-2.6.1/elf/dl-load.c:1567: undefined reference to `__stack_chk_fail_local'
/usr/src/glibc-2.6.1_build/elf/librtld.os:/usr/src/glibc-2.6.1/elf/dl-load.c:1787: more undefined references to `__stack_chk_fail_local' follow
collect2: ld returned 1 exit status
make[2]: *** [/usr/src/glibc-2.6.1_build/elf/ld.so] Error 1
make[2]: Leaving directory `/usr/src/glibc-2.6.1/elf'
make[1]: *** [elf/subdir_lib] Error 2
make[1]: Leaving directory `/usr/src/glibc-2.6.1'
make: *** [all] Error 2

```

I am building using a seperate build dir as suggested in the readme.

Any ideas ?

---


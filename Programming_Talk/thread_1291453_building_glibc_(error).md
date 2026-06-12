---
title: "building glibc (error)"
date: 2009-10-14
forum: Programming Talk
---

### Post by hsnm on 2009-10-14
I'm trying to build glibc but not as my primary library. I'm getting this error when making the package: 

../misc/syslog.c:123: sorry, unimplemented: inlining failed in call to ‘syslog’: function body not available
../misc/syslog.c:155: sorry, unimplemented: called from here
make[2]: *** [/home/hm/gcc/clib/build/misc/syslog.o] Error 1
make[2]: Leaving directory `/home/hm/gcc/clib/glibc-2.9/misc'
make[1]: *** [misc/subdir_lib] Error 2
make[1]: Leaving directory `/home/hm/gcc/clib/glibc-2.9'
make: *** [all] Error 2


Anybody has any idea?

---

### Post by hsnm on 2009-10-14
I tried to make this by --ignore-error and I got a new error: 

make[1]: [/home/hm/gcc/clib/build/libc_pic.os] Error 1 (ignored)
make[1]: *** No rule to make target `/home/hm/gcc/clib/build/elf/ld.so', needed by `/home/hm/gcc/clib/build/libc.so'.  Stop.
make[1]: Leaving directory `/home/hm/gcc/clib/glibc-2.9'
make: [all] Error 2 (ignored)

---


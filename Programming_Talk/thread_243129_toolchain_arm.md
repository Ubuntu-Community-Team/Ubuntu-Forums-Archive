---
title: "toolchain arm"
date: 2006-08-24
forum: Programming Talk
---

### Post by ryan_r on 2006-08-24
Hello,

I first tried to download the pre-compiled arm-linux-gcc tool(s) from [www.emdebian.org](www.emdebian.org). When i had breezy, it worked with no problems. But with the newest 6.06, I cannot install them based on wrong package versions ( gcc-base ). Any suggestions?

V3.3
cpp-3.3-arm-linux:
  Depends: gcc-3.3-base (<1:3.3.6) but 1:3.3.6-10 is to be installed

V3.4
cpp-3.4-arm-linux:
  Depends: gcc-3.4-base (<3.4.5) but 3.4.6-1ubuntu2 is to be installed


Next, i tried compiling my own toolchain based on [http://www.jerox.org/](http://www.jerox.org/). That has not worked either, it starts to fail with pthreads. Any suggestions?

In file included from ./gthr-default.h:1,
                 from ../../src/gcc/gthr.h:96,
                 from ../../src/gcc/unwind-dw2.c:42:
../../src/gcc/gthr-posix.h:43:21: pthread.h: No such file or directory
../../src/gcc/gthr-posix.h:44:20: unistd.h: No such file or directory
In file included from ./gthr-default.h:1,
                 from ../../src/gcc/gthr.h:96,
                 from ../../src/gcc/unwind-dw2.c:42:
../../src/gcc/gthr-posix.h:46: error: parse error before "__gthread_key_t"
../../src/gcc/gthr-posix.h:46: warning: type defaults to `int' in declaration of
 `__gthread_key_t'
../../src/gcc/gthr-posix.h:46: warning: data definition has no type or storage c
lass
../../src/gcc/gthr-posix.h:47: error: parse error before "__gthread_once_t"
../../src/gcc/gthr-posix.h:47: warning: type defaults to `int' in declaration of
 `__gthread_once_t'
../../src/gcc/gthr-posix.h:47: warning: data definition has no type or storage c
lass
../../src/gcc/gthr-posix.h:48: error: parse error before "__gthread_mutex_t"
../../src/gcc/gthr-posix.h:48: warning: type defaults to `int' in declaration of
 `__gthread_mutex_t'
../../src/gcc/gthr-posix.h:48: warning: data definition has no type or storage c
lass
../../src/gcc/gthr-posix.h: In function `__gthread_active_p':
../../src/gcc/gthr-posix.h:96: error: `pthread_create' undeclared (first use in
this function)
../../src/gcc/gthr-posix.h:96: error: (Each undeclared identifier is reported on
ly once
../../src/gcc/gthr-posix.h:96: error: for each function it appears in.)
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:456: error: parse error before '*' token
../../src/gcc/gthr-posix.h:456: error: parse error before ')' token
../../src/gcc/gthr-posix.h:465: error: parse error before '*' token
../../src/gcc/gthr-posix.h:465: error: parse error before ')' token
../../src/gcc/gthr-posix.h:471: error: parse error before "key"
../../src/gcc/gthr-posix.h:472: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_key_delete':
../../src/gcc/gthr-posix.h:472: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:473: warning: implicit declaration of function `pthre
ad_key_delete'
../../src/gcc/gthr-posix.h:473: error: `key' undeclared (first use in this funct
ion)
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:477: error: parse error before "key"
../../src/gcc/gthr-posix.h:478: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_getspecific':
../../src/gcc/gthr-posix.h:478: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:479: warning: implicit declaration of function `pthre
ad_getspecific'
../../src/gcc/gthr-posix.h:479: error: `key' undeclared (first use in this funct
ion)
../../src/gcc/gthr-posix.h:479: warning: return makes pointer from integer witho
ut a cast
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:483: error: parse error before "key"
../../src/gcc/gthr-posix.h:484: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_setspecific':
../../src/gcc/gthr-posix.h:484: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:485: warning: implicit declaration of function `pthre
ad_setspecific'
../../src/gcc/gthr-posix.h:485: error: `key' undeclared (first use in this funct
ion)
../../src/gcc/gthr-posix.h:485: error: `ptr' undeclared (first use in this funct
ion)
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:489: error: parse error before '*' token
../../src/gcc/gthr-posix.h:490: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_mutex_lock':
../../src/gcc/gthr-posix.h:490: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:492: warning: implicit declaration of function `pthre
ad_mutex_lock'
../../src/gcc/gthr-posix.h:492: error: `mutex' undeclared (first use in this fun
ction)
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:498: error: parse error before '*' token
../../src/gcc/gthr-posix.h:499: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_mutex_trylock':
../../src/gcc/gthr-posix.h:499: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:501: warning: implicit declaration of function `pthre
ad_mutex_trylock'
../../src/gcc/gthr-posix.h:501: error: `mutex' undeclared (first use in this fun                                 ction)
../../src/gcc/gthr-posix.h: At top level:
../../src/gcc/gthr-posix.h:507: error: parse error before '*' token
../../src/gcc/gthr-posix.h:508: warning: function declaration isn't a prototype
../../src/gcc/gthr-posix.h: In function `__gthread_mutex_unlock':
../../src/gcc/gthr-posix.h:508: warning: old-style parameter declaration
../../src/gcc/gthr-posix.h:510: warning: implicit declaration of function `pthre                                 ad_mutex_unlock'
../../src/gcc/gthr-posix.h:510: error: `mutex' undeclared (first use in this fun                                 ction)
make[4]: *** [libgcc/./unwind-dw2.o] Error 1
make[4]: Leaving directory `/usr/src/gcc-arm-linux-3.4.3/build/gcc'
make[3]: *** [libgcc.a] Error 2
make[3]: Leaving directory `/usr/src/gcc-arm-linux-3.4.3/build/gcc'
make[2]: *** [all-gcc] Error 2
make[2]: Leaving directory `/usr/src/gcc-arm-linux-3.4.3/build'
s=`cat status`; rm -f status; test $s -eq 0
make[1]: *** [stamps/05-build-stamp] Error 1
make[1]: Leaving directory `/usr/src/gcc-arm-linux-3.4.3'
make: *** [stamps/05-build-stamp] Error 2
debuild: fatal error at line 768:
dpkg-buildpackage failed!

](*,)

---


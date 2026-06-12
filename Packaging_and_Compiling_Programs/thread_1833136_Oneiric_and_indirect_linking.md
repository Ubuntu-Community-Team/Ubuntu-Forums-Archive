---
title: "Oneiric and indirect linking"
date: 2011-08-25
forum: Packaging and Compiling Programs
---

### Post by pressureman on 2011-08-25
I'm at my wit's end trying to get Freeswitch ([www.freeswitch.org](www.freeswitch.org)) to compile on Oneiric.

It fails to compile with errors such as:

```

./libesl.a(esl_threadmutex.o): In function `esl_thread_create_detached_ex':
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:116: undefined reference to `pthread_attr_setstacksize'
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:118: undefined reference to `pthread_create'
./libesl.a(esl_threadmutex.o): In function `esl_mutex_create':
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:149: undefined reference to `pthread_mutexattr_init'
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:152: undefined reference to `pthread_mutexattr_settype'
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:161: undefined reference to `pthread_mutexattr_destroy'
./libesl.a(esl_threadmutex.o): In function `esl_mutex_trylock':
/usr/src/freeswitch/libs/esl/src/esl_threadmutex.c:207: undefined reference to `pthread_mutex_trylock'
../../libs/libedit/src/.libs/libedit.a(term.o): In function `term_move_to_char':
/usr/src/freeswitch/libs/libedit/src/term.c:650: undefined reference to `tgoto'
/usr/src/freeswitch/libs/libedit/src/term.c:650: undefined reference to `tputs'

```

... and so on.

It compiles fine on an up-to-date Debian Wheezy installation, so I figure it's got to be something fairly subtle in Oneiric's gcc/ld defaults.

I tried compiling with CFLAGS=-Wl,--copy-dt-needed-entries,--no-as-needed to try to revert the behaviour described here [https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition](https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition) but to no success.

I had this problem on Natty during the beta phase too, and got around it by using gcc 4.4 instead of 4.5 (and later 4.6). After a while, I gave it a try with 4.6 again, and it was ok (I suspect when they must have reverted the --as-needed default).

But with Oneiric, it just a big case of fail at the moment. What has Ubuntu done to gcc to make it so picky?

Any help greatly appreciated.

---

### Post by pressureman on 2011-09-01
Nevermind, fixed it after changing order of libs passed to linker.

---

### Post by MadCow108 on 2011-09-01
just for future reference as this is a common problem:

oneiric uses the linker flag --as-needed by default. With this flag correct ordering of libraries and objects on the commandline is important.
objects needing symbols must be placed before libraries providing them.
E.g. file.o and staticlib.a need symbols from libm:
wrong:
```
gcc -lm file.o staticlib.a
```
gcc will think libm is not needed and drops it, when it later encounters the objects needing it you will get undefined references
right:
```
gcc file.o staticlib.a -lm
```

Important for autotools makefiles. Place libraries into LIBS or LDADD variables, **not** in LDFLAGS

---


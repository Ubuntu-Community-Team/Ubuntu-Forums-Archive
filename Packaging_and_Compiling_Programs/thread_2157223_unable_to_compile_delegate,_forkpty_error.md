---
title: "unable to compile delegate, forkpty error"
date: 2013-06-24
forum: Packaging and Compiling Programs
---

### Post by NiteRain on 2013-06-24
Been trying to compile delegate for a while.  There seems to be an issue with forkpty.  This is what I get back:

```
[INDENT]cc  -L../lib -o embed embed.o version.o ../srcsign.o \[/INDENT]
[INDENT]            ../lib/library.a ../lib/libcfi.a ../lib/libmimekit.a ../lib/libmd5.a \[/INDENT]
[INDENT]            -lnsl -ldl -lutil -lpthread -lstdc++ -lc ../lib/libsubst.a[/INDENT]
[INDENT]../lib/libsubst.a(_-forkpty.o): In function `_ForkptyX(int*, char*, void*, void*)':[/INDENT]
[INDENT]_-forkpty.c:(.text+0x1): undefined reference to `forkpty'[/INDENT]
[INDENT]../lib/libsubst.a(_-forkpty.o): In function `_Forkpty(int*, char*)':[/INDENT]
[INDENT]_-forkpty.c:(.text+0x15): undefined reference to `forkpty'[/INDENT]
[INDENT]collect2: error: ld returned 1 exit status[/INDENT]
[INDENT]make[2]: *** [embed] Error 1[/INDENT]
[INDENT]make[2]: Leaving directory `/home/unknownuser/Downloads/delegate9.9.8-pre20/src'[/INDENT]
[INDENT]make[1]: *** [start0] Error 2[/INDENT]
[INDENT]make[1]: Leaving directory `/home/unknownuser/Downloads/delegate9.9.8-pre20/src'[/INDENT]
[INDENT]mkmake: ERROR LOG is left at /home/unknownuser/Downloads/delegate9.9.8-pre20/src/mkmake.err[/INDENT]
[INDENT]mkmake: ERROR LOG is left at /home/unknownuser/Downloads/delegate9.9.8-pre20/src/mkmake.err[/INDENT]
[INDENT]make: *** [all] Error 2[/INDENT]

```

---


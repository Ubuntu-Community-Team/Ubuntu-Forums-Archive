---
title: "cant use pthreads,"
date: 2011-10-26
forum: Packaging and Compiling Programs
---

### Post by newkie on 2011-10-26
Hello,
I am getting trouble to use the pthread.h.

i got inside my code:
 #include <pthread.h>

```

 file /usr/include/pthread.h
/usr/include/pthread.h: ASCII C program text

```

(it is there)

when i try to compile it:

```

techmago@LuisSony ~ $ gcc -lpthread teste.c 
/tmp/ccQo11xG.o: In function `main':
teste.c:(.text+0x39): undefined reference to `pthread_create'
teste.c:(.text+0x61): undefined reference to `pthread_create'
teste.c:(.text+0x89): undefined reference to `pthread_create'
teste.c:(.text+0xb1): undefined reference to `pthread_create'
teste.c:(.text+0xc9): undefined reference to `pthread_join'
teste.c:(.text+0xdd): undefined reference to `pthread_join'
teste.c:(.text+0xf1): undefined reference to `pthread_join'
teste.c:(.text+0x105): undefined reference to `pthread_join'
collect2: ld returned 1 exit status

```

i am with the last ubuntu (11.10) Which packtage i am missing?
with the ubuntu 10.4 is the same.

---

### Post by MadCow108 on 2011-10-26
it should be:
```
gcc -pthread teste.c 
```

if you don't want the general pthread variable (which makes a couple other things threadsafe, so its recommended) but only need libpthread you need to place it behind the object/source file like with static libraries:

```
gcc  teste.c -lpthread
```

this is due to the linker flag --as-needed beeing enabled by default in ubuntu 11.10, see man ld

---

### Post by newkie on 2011-10-27
ok, thank you, this solve the issue. but why?

whats the big difference between

```

gcc teste.c -lpthread (which work)
gcc -lpthread teste.c (which have linking problems)

```

And why, in some system both work?
I got no issues with that order in my college computer (some ubuntu, not the latest) and in my server (centOS 5.7)

---

### Post by MadCow108 on 2011-10-27
gcc/ld scan the command line left to right.
it finds libpthread, does not know of anything that needs it so it forgets about it.
Then it finds the source file, compiles it, registers the symbols its need and continues, but no libpthread is following to provide the symbols and the one before it has forgotten so you get an error.
It will only forget unneeded libraries when the ld flag --as-needed is used. This is only default on ubuntu >= 11.10 (and I think mandriva). No other distros I know of uses that flag.

I think the reason for this dumb behavior is performance, it has always done the same this static libraries.

---


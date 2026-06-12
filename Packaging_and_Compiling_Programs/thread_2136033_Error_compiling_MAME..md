---
title: "Error compiling MAME."
date: 2013-04-16
forum: Packaging and Compiling Programs
---

### Post by Cheesemill on 2013-04-16
Hi there guys,

One of the private trackers that I'm a member of has just started running arcade machine gaming competitions. To be able to enter I need to run a specific version of MAME (WolfMAME 0.148).

I can't find any pre-built binaries for my system so I'm trying to compile it myself using the official MAME source ([here]("http://mamedev.org/release.html")) and the WolfMAME patches ([here]("http://wolfmame.marpirc.net/")).
I should have all of the dependencies as I've already run 'sudo apt-get build-dep mame', but when I run the make command it fails with the following error...
```
Linking mame64...
/usr/bin/ld: obj/sdl64/libocore.a(sdlsync_tc.o): undefined reference to symbol 'pthread_mutexattr_settype@@GLIBC_2.2.5'
/usr/bin/ld: note: 'pthread_mutexattr_settype@@GLIBC_2.2.5' is defined in DSO /lib/x86_64-linux-gnu/libpthread.so.0 so try adding it to the linker command line
/lib/x86_64-linux-gnu/libpthread.so.0: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make: *** [mame64] Error 1
```

I've tried building the vanilla source without the patches and this fails in the same way, so it's a MAME issue rather than a problem with WolfMAME.

Any ideas/suggestions would be very welcome.

---

### Post by mc4man on 2013-04-16
You could try adding this to your ./configure - (or some variation of ? like lgthread-2.0, ect.
```
LDFLAGS=-lpthread-2.0
```

---

### Post by Magicantian on 2013-05-19
I too am having the same issue as Original Poster.  How do I go about adding "LDFLAGS=-lpthread-2.0"? OP, did this solution work for you?   I am currently on Xubuntu 13.04 x64 and have compiled MAME successfully on Lubuntu 12.04 & 12.10 x64.  

Edit: also wanted to menton that I am only using a Vanilla 0.148 source code with no nag patch.

---

### Post by oldos2er on 2013-05-19
Moved to Packaging & Compiling Programs.

---


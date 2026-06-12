---
title: "[SOLVED] Compiling acerhk modules - scripting"
date: 2008-08-21
forum: Packaging and Compiling Programs
---

### Post by pmsumner on 2008-08-21
Hi, first off I apologise, I think this is in the wrong subforum.

I'm trying to compile the acerhk module in a script.  The remainder of my script has to be run under sudo (removing modules, reinserting modules etc) and I'm finding that running make under sudo fails:

```
phil@home-laptop:/usr/src/acerhk-0.5.35$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [acerhk.ko] Error 2
```

However, running the same command as my "normal" login works:

```
phil@home-laptop:/usr/src/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /usr/src/acerhk-0.5.35/acerhk.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/acerhk-0.5.35/acerhk.mod.o
  LD [M]  /usr/src/acerhk-0.5.35/acerhk.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
```

I've also tried it using sudo -u $USER make

```
phil@home-laptop:/usr/src/acerhk-0.5.35$ sudo -u phil make
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
rm: cannot remove `include/config/kernel.release': Permission denied
make[1]: *** [include/config/kernel.release] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [acerhk.ko] Error 2
```

Can anyone explain for me why this should be and how I can work around it?

Thanks!
Phil

---

### Post by pmsumner on 2008-08-22
I fixed this with the diff found in this ticket:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/53953](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/53953)

---


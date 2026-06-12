---
title: "problem installing sctplib"
date: 2010-12-01
forum: Packaging and Compiling Programs
---

### Post by soultrav on 2010-12-01
Hello,

I downloaded the package sctplib-1.0.9 for installing headers and libraries needed to develop SCTP-based programs.
After running './configure' (all went well), I get the following error after make:

```
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DLINUX -Wall -g3 -O0 -D_REENTRANT -D_THREAD_SAFE -MT adaptation.lo -MD -MP -MF .deps/adaptation.Tpo -c -o adaptation.lo adaptation.c
../../libtool: xrealloc: ../bash/subst.c:658: cannot allocate 67108864 bytes (805371904 bytes allocated)
make[3]: *** [adaptation.lo] Error 2
```

Any ideas what this could be?

PS: isn't lksctp-tools supposed to be sufficient for developing SCTP programs? I already have the package installed, but I found no libraries or headers in /usr/local/lib or /usr/include respectively.

---

### Post by SevenMachines on 2010-12-02
> **soultrav said:**
> Hello,

I downloaded the package sctplib-1.0.9 for installing headers and libraries needed to develop SCTP-based programs.
After running './configure' (all went well), I get the following error after make:

```
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DLINUX -Wall -g3 -O0 -D_REENTRANT -D_THREAD_SAFE -MT adaptation.lo -MD -MP -MF .deps/adaptation.Tpo -c -o adaptation.lo adaptation.c
../../libtool: xrealloc: ../bash/subst.c:658: cannot allocate 67108864 bytes (805371904 bytes allocated)
make[3]: *** [adaptation.lo] Error 2
```Any ideas what this could be?

xrealloc is about reallocating memory blocks, i'm not sure why libtool's failing here, i imagine its not about the source though and maybe more a tools or system thing, not sure sorry. source compiles fine here on maverick i386

> 
PS: isn't lksctp-tools supposed to be sufficient for developing SCTP programs? I already have the package installed, but I found no libraries or headers in /usr/local/lib or /usr/include respectively.When you want to develop with a library, look for a package with a -dev extension, in this case search for 'sctp dev' in synaptic or equivalent and you'll find you need the package
```
$ sudo apt-get install libsctp-dev
$ dpkg -L libsctp-dev |grep include
/usr/include
/usr/include/netinet
/usr/include/netinet/sctp.h

```

---

### Post by soultrav on 2010-12-02
I didn't manage to figure out why xrealloc was failing, but installing libsctp-dev worked perfectly!

Thanks!!

---


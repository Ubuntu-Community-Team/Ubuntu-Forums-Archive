---
title: "Building A Linux System"
date: 2007-12-14
forum: Programming Talk
---

### Post by startherepodcast on 2007-12-14
Hey,

Can Anyone help me please. A while ago I tried the tutorial at the link below on creating a tiny embedded Linux system but it wouldn't work. Can Anyone tell me if this should work or if there's anything else I need to know.

The URL Is: [http://www.linuxdevices.com/articles/AT9416075241.html]("http://www.linuxdevices.com/articles/AT9416075241.html")

Thanks

---

### Post by geraldm on 2007-12-15
I have met Bruce, and when he publishes an article saying what that does, then that is what it has done.  He is well known in the Linux community.  Note the old date of 2001.  If I remember correctly,
Bruce was the original author of busybox.
You seem to have digressed from the article, in that you say you built an embedded system ?   Did I misjudge that?
Where did your build not do what was expected, and what did you get as a result that was different?

Gerald

---

### Post by startherepodcast on 2007-12-15
Thanks For Your Reply,

I am going to try going through all the steps again today and see wether it will work this time. If not i'll post back here with any errors.

---

### Post by startherepodcast on 2007-12-15
Right,

I have now reached the stage where you compile a static-Linked Busybox. When I try to compile Busybox This Is What I Get:

```
adzon@adzon-desktop:~/Desktop/busybox-1.8.2$ make
  SPLIT   include/autoconf.h -> include/config/*
  GEN     include/bbconfigopts.h
  HOSTCC  applets/usage
  GEN     include/usage_compressed.h
  CC      applets/applets.o
applets/applets.c:15:2: warning: #warning Static linking against glibc produces buggy executables
applets/applets.c:16:2: warning: #warning (glibc does not cope well with ld --gc-sections).
applets/applets.c:17:2: warning: #warning See sources.redhat.com/bugzilla/show_bug.cgi?id=3400
applets/applets.c:18:2: warning: #warning Note that glibc is unsuitable for static linking anyway.
applets/applets.c:19:2: warning: #warning If you still want to do it, remove -Wl,--gc-sections
applets/applets.c:20:2: warning: #warning from top-level Makefile and remove this warning.
applets/applets.c:21:2: error: #error Aborting compilation.
make[1]: *** [applets/applets.o] Error 1
make: *** [applets] Error 2
```

If someone could tell me the answer to this I would be very Grateful

Tanks...

---

### Post by geraldm on 2007-12-16
I think you need to look at all of the options which were to be passed to    the compiler.  Remove the options that were suggested.
Read the bug report to know what problems static linking might provide to your executable.

Gerald

---

### Post by nitro_n2o on 2007-12-16
here is another option if you would like to start from scratch [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by startherepodcast on 2007-12-21
Hi,

I Already Tried LFS. It seemed to work ok but for what I would like it seems a bit bloated. A few days ago I found buildroot that I think will suit my needs well.

Thanks for all your help...

---


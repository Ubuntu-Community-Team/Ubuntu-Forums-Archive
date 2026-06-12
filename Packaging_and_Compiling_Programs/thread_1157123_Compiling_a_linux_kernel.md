---
title: "Compiling a linux kernel"
date: 2009-05-12
forum: Packaging and Compiling Programs
---

### Post by Nam Ninh on 2009-05-12
I am learning how to build a kernel module.

First, I tried to create .config file by issuing a command:
/usr/src/linux.../make config

I got an error:

/usr/src/linux-headers-2.6.24-23$ make config
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:399: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied
compilation terminated.
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
nam@bayview:/usr/src/linux-headers-2.6.24-23$ 


Any help would be appriciated.

Thanks.

---

### Post by johnl on 2009-05-12
I would not try to build the source code at that directory in your system (/usr/src) -- that directory is owned by root.

What you should do is check out / obtain a copy of the kernel you want to build in your home directory.  Then you can configure and build the kernel without messing with permissions and such.

To get the Ubuntu kernel source:

```

johnl@reznor:~ $ apt-get source linux-image-`uname -r`

```

Hope this helps.

---


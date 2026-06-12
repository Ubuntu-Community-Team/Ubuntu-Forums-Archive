---
title: "Using Gcc version 3.4 with Ubuntu 8.10"
date: 2009-05-28
forum: Programming Talk
---

### Post by abhilash82 on 2009-05-28
Is it possible to install and use 
gcc version 3.4.6 20060404 and GNU C Library version 2.3.4 in Ubuntu 8.10?

I have to use the above versions for my compilation.

If it is not possible with Ubuntu 8.10, then please suggest a suitable Ubuntu version which would enable me to do so.

---

### Post by regala on 2009-05-28
> **abhilash82 said:**
> Is it possible to install and use 
gcc version 3.4.6 20060404 and GNU C Library version 2.3.4 in Ubuntu 8.10?

I have to use the above versions for my compilation.

If it is not possible with Ubuntu 8.10, then please suggest a suitable Ubuntu version which would enable me to do so.

as for gcc 3.4.6, you can download the sources from [ftp://ftp.gnu.org/gnu](ftp://ftp.gnu.org/gnu)
and build it, (./configure + make bootstrap cmdline spell wizardry)

but, I fail to see why you would _need_ glibc 2.3.4.
changing the libc on a system is not "simple", as for what I know, replacing your current glibc with a lower version one, will definitly break all the binaries running on your box (which are linked against glibc 2.7, IIRC). if not impossible, it's lethal for your system.

You can try a chroot, but this is quite long to explain here. google can help you with the search "gcc toolchain chroot".

maybe I am rude, but _why_ would you need to compile something against a lower glibc which is quite "old". are you cross-compiling ?

PS: the version of Ubuntu you would need was Ubuntu 5.10, the Breezy Badger, which is not supported, nor available for download, I guess.

---

### Post by ssam on 2009-05-28
you can get old ubuntu releases from
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

it may be best to install the old release in a virtual machine, as it may not have support for your hardware. it may also be worth doing a minimal or server install, if you dont need a gui on it.

---


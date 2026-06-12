---
title: "[ERROR] Compiling Kernel 3.17"
date: 2014-11-04
forum: Packaging and Compiling Programs
---

### Post by jgilfn on 2014-11-04
Greetings,

I have compiled kernels many time before, but now I'm getting this error:

"make: *** [debian/stamp/build/kernel] Error 2"

I used this command to compile: 
sudo MAKEFLAGS="HOSTCC=/usr/bin/gcc CCACHE_PREFIX=distcc" make-kpkg --rootcmd fakeroot -j8 --verbose --initrd --append-to-version=-x86-64 kernel_image kernel_headers

This is a kernel patched with aufs and pf-kernel

This gives me the same error when compiling a simple unpatched kernel. (3.17 and 3.16)

Verbose output of this command: (latest 800 lines)

[https://mega.co.nz/#!IYZAlKqS!CtZ774yhg1PeiQxvAoJl7fQ43H51EUYfdbUztkhS0_Q](https://mega.co.nz/#!IYZAlKqS!CtZ774yhg1PeiQxvAoJl7fQ43H51EUYfdbUztkhS0_Q)

I'm using Ubuntu 14.04 Trusty Tahr.

Does anybody know how to fix this?

Thank you in advance...

---


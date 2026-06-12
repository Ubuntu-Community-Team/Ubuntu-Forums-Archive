---
title: "How can I get older packages of the GNU toolchain"
date: 2005-10-21
forum: Programming Talk
---

### Post by scottlove on 2005-10-21
I just installed ubuntu 5.10.

I am working on a project that requires an older version of the GNU toolchain (specifically gcc and libc).  I can't remember the version as I type this (it was the version that came with RedHat 9), but don't know how to go about installing this older version.

I have not yet installed the new development libraries on my machine. 

Any help would be appreciated.:)

---

### Post by toojays on 2005-10-22
Your local [GNU FTP mirror]("http://www.gnu.org/prep/ftp.html") should have original GNU versions going back many years. If you need patches which are specific to RedHat, you are probably better off asking in a RedHat specific forum . . . I imagine someone could point to you a source RPM which contains the patches you want.

If you install an old libc over the top of libc from Ubuntu 5.10, you will probably break your system. Have a look at the man page for chroot, this may be able to help you do what you want while leaving your Ubuntu install intact.

---


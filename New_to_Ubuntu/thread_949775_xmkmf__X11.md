---
title: "xmkmf  X11"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by johanang on 2008-10-16
Vnc Server xmkmf error
According to the manual i need to create the JPEG and zlib library's. Read Write Permissions were given to everything in the vnc_unixsrc folder.

As instructed in the VNCServer manual i am to run:
Sudo xmkmf in the /vnc_unixsrc folder.

I receive the following errors:

ubuntu@ubuntu:~/vnc_unixsrc$ sudo xmkmf
mv -f Makefile Makefile.bak
imake -DUseInstalled -I/usr/lib/X11/config
<stdin>:1:19: error: stdio.h: No such file or directory
<stdin>:2:19: error: ctype.h: No such file or directory
<stdin>: In function âmainâ:
<stdin>:18: error: âNULLâ undeclared (first use in this function)
<stdin>:18: error: (Each undeclared identifier is reported only once
<stdin>:18: error: for each function it appears in.)
<stdin>:45: warning: incompatible implicit declaration of built-in function âssc
anfâ
<stdin>:49: warning: incompatible implicit declaration of built-in function âpri
ntfâ
Aborted

Any Idea's

---


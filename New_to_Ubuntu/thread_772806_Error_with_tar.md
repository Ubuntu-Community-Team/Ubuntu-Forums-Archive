---
title: "Error with tar"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by vijaycm on 2008-04-28
Hi,

I have installed ubuntu desktop 8.04, I am trying to extract compressed files. I throws this error. I get the same error on command line or archive manager. Please help.

tar -xvvf index.htm.tar
tar: Ignoring unknown extended header keyword `SCHILY.dev'
tar: Ignoring unknown extended header keyword `SCHILY.ino'
tar: Ignoring unknown extended header keyword `SCHILY.nlink'
-rw-rw-rw- 2643817/552    8527 2007-06-12 21:14 index.htm

-Thx.

---

### Post by Monicker on 2008-04-28
> **vijaycm said:**
> Hi,

I have installed ubuntu desktop 8.04, I am trying to extract compressed files. I throws this error. I get the same error on command line or archive manager. Please help.

tar -xvvf index.htm.tar
tar: Ignoring unknown extended header keyword `SCHILY.dev'
tar: Ignoring unknown extended header keyword `SCHILY.ino'
tar: Ignoring unknown extended header keyword `SCHILY.nlink'
-rw-rw-rw- 2643817/552    8527 2007-06-12 21:14 index.htm

-Thx.

Strange. This does not seem to be something specific to Ubuntu.  

These links MIGHT give some insight:

[http://www.directadmin.com/forum/showthread.php?t=20814]("http://www.directadmin.com/forum/showthread.php?t=20814")

[http://www.directadmin.com/forum/showthread.php?t=21759]("http://www.directadmin.com/forum/showthread.php?t=21759")

I glanced through them,but it seems to be the typical vendor finger pointing in action.

---


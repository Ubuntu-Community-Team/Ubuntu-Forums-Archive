---
title: "making my own linux"
date: 2008-10-03
forum: Other OS Talk
---

### Post by AnLGP on 2008-10-03
hello,

I'm attempting to follow LFS.  I've got the partition set up and mounted.  I'm  up to downloading the necessary packages.  I want to use busybox.  Can anyone tell me if the list on LFS is up to date?  Thanks.

---

### Post by Sorivenul on 2008-10-03
Not entirely sure what you mean by "up to date".  If you mean does it use all the most current packages, then the answer is no.  If you man is the list in the book current, then yes, as it has been tested.

If you are going to use BusyBox, I'm also assuming you plan on substituting uClibc.  If that is the case and you haven't already read [this]("http://www.linuxfromscratch.org/hints/downloads/files/uclibc.txt").  Though slightly outdated, the method should still apply and the patches look like they are existant and relatively up to date.  There is also a method of compiling LFS this way outlined [here]("http://www.uclibc.org/lists/busybox/2004-May/011538.html"), though the info is for 5.0, I'm sure it is relatively easily modified for the current release.

Good luck!

---


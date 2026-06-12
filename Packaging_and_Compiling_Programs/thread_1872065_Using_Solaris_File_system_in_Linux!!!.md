---
title: "Using Solaris File system in Linux???!!!"
date: 2011-10-30
forum: Packaging and Compiling Programs
---

### Post by hosseinz80500 on 2011-10-30
Hi.
I am using LFS book to create my linux distro. I want to use solaris file system such as ZFS file system in my distro. I am researching about Virtual file system in linux kernel and I think this layer cause porting to any other file system from other operating system. is it possible????

---

### Post by MadCow108 on 2011-11-01
zfs can be used as a real file system on linux since a while:
[http://zfsonlinux.org/](http://zfsonlinux.org/)

see the faq for why you don't need to use a virtual file system anymore:
[http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue](http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue)

---


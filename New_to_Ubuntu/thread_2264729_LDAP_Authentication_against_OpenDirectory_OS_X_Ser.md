---
title: "LDAP Authentication against OpenDirectory OS X Server 10.9"
date: 2015-02-09
forum: New to Ubuntu
---

### Post by olePigeon on 2015-02-09
Hello,

A warning: I've never used Linux before and I've been thrown into it heads first at work.  I'm a computer tech at a local junior high school and we have about 15 Core Duo iMacs.  They can only run OS X 10.6, which is just too old.  There're no recent security updates for it, so they're subject to heartbleed and other more recent security issues.  I'm a little worried about letting the students use them on the internet.  Perfectly useable computers, decent hardware, but no longer supported by Apple.

So after a lot of trouble, I finally got Lubuntu installed on an iMac using a special "Mac version" to cope with the (apparently) bad implementation of BIOS emulation in Apple's EFI.

I followed this useful tutorial:

[https://www.youtube.com/watch?v=l0e8rG0mku8](https://www.youtube.com/watch?v=l0e8rG0mku8)

And it's gotten me as far as using the getent passwd command to list all my Open Directory accounts.  My OS X Server sees the computer and I've added it to my student group.  However, it *still* won't let me  su  or login with any of the OD users.  It tells me "No passwd entry for user '<user>'."  I can use ldapsearch and look up individual users, so it's definitely connecting the OD server.  I'm not sure what's going on.

Following the official tutorial on the Ubuntu website results in the computer unable to log in even when using local accounts.  It's also about 5 versions too old for OS X Server.

---

### Post by olePigeon on 2015-02-10
Wasn't expecting an answer, frankly.  Information regarding this particular scenario is pretty scarce.  Even our own Apple Rep didn't have an answer.

---


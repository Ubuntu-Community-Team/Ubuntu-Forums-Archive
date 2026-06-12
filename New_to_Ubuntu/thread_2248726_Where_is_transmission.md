---
title: "Where is transmission"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by LiftingReallyMatte on 2014-10-16
Hello everyone
transmission suddenly disappeared from my PC
So I reinstalled it
however I can't locate it on the bin folder
any idea where I can find it's .gtk file?
Many thanks

---

### Post by Vladlenin5000 on 2014-10-16
Hi, welcome.

Software don't disappear, suddenly or otherwise, unless it's uninstalled.
And how exactly have you reinstalled?

---

### Post by papibe on 2014-10-16
Hi LiftingReallyMatte. Welcome to the forum ):P

The program itself is located in /usr/bin and it's named transmission-gtk

Here are a few useful commands:

Get the list of installed packages and filter the ones with transmission on the name:
```
$ dpkg -l | grep transmission
ii  transmission-common                                   2.82-1.1ubuntu3.1                                   all          lightweight BitTorrent client (common files)
ii  transmission-gtk                                      2.82-1.1ubuntu3.1                                   amd64        lightweight BitTorrent client (GTK+ interface)

```
Know if a package is installed and what version do you have:
```
$ apt-cache policy transmission-gtk 
transmission-gtk:
  Installed: 2.82-1.1ubuntu3.1
  Candidate: 2.82-1.1ubuntu3.1
  Version table:
 *** 2.82-1.1ubuntu3.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.82-1.1ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```
Locate a binary, or related, on the system:
```
$ whereis transmission-gtk 
transmission-gtk: /usr/bin/transmission-gtk /usr/bin/X11/transmission-gtk /usr/share/man/man1/transmission-gtk.1.gz
```
Does that help? Let us know if you have more questions.
Regards.

---

### Post by LiftingReallyMatte on 2014-10-16
Thank you papibe :) Helped me out a lot.
Vladlenin I'm aware, but it was simply gone and I'm certain that I have not unintstalled anything.

---

### Post by ian-weisser on 2014-10-16
> **LiftingReallyMatte said:**
> So I reinstalled it

That's worrisome, if it wasn't uninstalled.
Does this mean you now have two Transmissions, from two different sources, installed two different ways?
That could cause problems.

---


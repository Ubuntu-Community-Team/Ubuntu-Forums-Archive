---
title: "AMD64: Hear multiple sounds using Both ESD &amp; ALSA"
date: 2005-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Leira on 2005-05-23
first of all, u should follow this [HOWTO: Hear multiple sounds using Both ESD & ALSA](http://www.ubuntuforums.org/showthread.php?t=32063&page=1&pp=10), except the first about libesd-alsa0, cause u will find there is no such a libesd-alsa0 package of amd64 arch. i've tried compile a amd64 package by my self from the src package, but it was not workable either. and maybe that is why it is not included in official packages.

but here is a temporary solution to use esd with aoss (absolutely temporary, cause i cannot find where gnome start esd):

1. mv /usr/bin/esd /usr/bin/esd.orig
2. make a script /usr/bin/esd:
```
#!/bin/sh aoss

/usr/bin/esd.orig $*
```
3. chmod a+x /usr/bin/esd

now, it just can work, and the gnome's event sound as well.

---

### Post by Leira on 2005-05-24
posted in wrong place, i reposted it in AMD64-User

---


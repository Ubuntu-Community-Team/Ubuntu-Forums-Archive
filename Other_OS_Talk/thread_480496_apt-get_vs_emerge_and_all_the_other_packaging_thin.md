---
title: "apt-get vs emerge and all the other packaging thingy out there"
date: 2007-06-21
forum: Other OS Talk
---

### Post by maddot on 2007-06-21
Okay, what i think is the main diffrence between each distro is the way the packagingis handled and the updating? Like gentoo based uses emerge and debian based uses apt-get. So what's stopping the developers from making a one single unified package managing system? OR one unified standard for linux packages? Also, is it possible to have say ubuntu, be able to emerge and do apt-get?

---

### Post by ThinkBuntu on 2007-06-21
All I know is that
```
# pacman -Syu
```
makes me happy. One of those features that would be nice in Debian (and Ubuntu, et. al) would be a single command to update and upgrade. Same goes for
```
# pacman -Sy inkscape
```
Updates and installs in one fell swoop.

---

### Post by RedDwarf on 2007-06-21
> **maddot said:**
> So what's stopping the developers from making a one single unified package managing system? OR one unified standard for linux packages?
That would be a lot of work... for a _little_ reward. 
Every distro using the same package format doesn't means that a package from Mandriva would work with Fedora. So, why a distro would want to do the work?

---

### Post by Cene on 2007-06-21
emerge --sync && emerge -uDav world
Makes me happy. :]

---


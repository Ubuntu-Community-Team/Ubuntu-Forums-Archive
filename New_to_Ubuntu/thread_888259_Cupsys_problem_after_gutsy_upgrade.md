---
title: "Cupsys problem after gutsy upgrade"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by kcoylenet on 2008-08-12
I was doing updates to gutsy gibbon, and I keep getting this error:

dpkg: error processing cupsys (--configure):
subprocess post-installation script returned error exit status 1

I've done apt-get -f install a number of times and this keeps happening. I tried:

apt-get -r cupsys

and got

hplip depends on cupsys (>= 1.1.20).
ubuntu-desktop depends on cupsys.
cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
Package cupsys is to be removed.
Package cups is not installed.
bluez-cups depends on cupsys.
hal-cups-utils depends on cupsys.
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
dpkg: error processing cupsys (--remove):
dependency problems - not removing

Now I can't install any packages because I keep getting this error. Anyone know of a way to fix it?

Thanks,
kc

---

### Post by kcoylenet on 2008-08-20
This is now being discussed in a new thread:

[http://ubuntuforums.org/showthread.php?t=894480](http://ubuntuforums.org/showthread.php?t=894480)

---


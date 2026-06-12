---
title: "&quot;Could not calculate the upgrade&quot;"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by pjbeahan on 2011-10-22
I'm trying to upgrade to version 11.10, but have been wrestling with the error "Could not calculate the upgrade" for a week with no results. 

```
patrick@patrick-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libgcc1 : Depends: gcc-4.6-base (= 4.6.1-9ubuntu3) but 4.6.1-14 is to be installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
patrick@patrick-desktop:~$ 

```

I've tried to go back to only original repositories, and that didn't change anything. I tried using aptitude? from some terminal commands in another thread, and that only made the error message come up instantly, whereas before it was at least setting up for a while before falling on its face.

---

### Post by LinuxFan999 on 2011-10-22
Which version of Ubuntu are you using right now?

---

### Post by pjbeahan on 2011-10-22
natty, 11.04

---

### Post by LinuxFan999 on 2011-10-22
You should back up your data, then download Ubuntu 11.10 and burn the ISO image to a CD, then reboot with the CD inserted and do a clean installation of Ubuntu 11.10. When the installation is finished, you can move your files back to the /home partition.

---

### Post by pjbeahan on 2011-11-12
Not the way I wanted to do it, but I did and it worked. Thanks for the help, though! Thank goodness for Ubuntu 1, made backing up the files very easy!

---


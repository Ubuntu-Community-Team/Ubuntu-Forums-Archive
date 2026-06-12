---
title: "Booting problems.. and backup problems"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by laurielegit on 2008-07-18
My problem started one night. I was buying a Nintendo DS off Ebay, and everything went smoothly. I shut the computer down and turned it off at the mains.
When I tried to start it up the morning after it went through its grub routine and finally got round to starting Ubuntu. except it didn't. I was greeted with a message telling me that it had encountered error 2 and ubuntu was a unreadable file or directory. this signifies to me that ubuntu has become corrupted in some way or another... this is _***not***_ my real problem.

I need to assess my old home folder and retrieve my documents. I am currently working on copy of fedora that I used formerly. some time in the past, when install a program of some kind, I was instructed to use a command line that let me assess all folders with the power to change any of the properties. I have the root password for both systems, I just need to find a way to utilise this asset. think of it like having a bike but being told you can only walk.

anyway... this is a matter of importance to me.. also, if anyone could tell me why Ubuntu failed I would appreciate it as I have been told if ubuntu is not made stable windows xp will replace it....

---

### Post by bumanie on 2008-07-18
As for why, I have no idea if it was shutdown properly - ??an electricity surge when you switched off the power point??? Total guess that sounds unlikely. As for graphical superuser mode in fedora - I think it is > gksu nautilus - Fedora uses gnome like ubuntu, so I assume the file manager is nautilus. gksu should give graphical superuser mode. Ever need the same function in ubuntu gksudo nautilus

---

### Post by wpshooter on 2008-07-18
> **laurielegit said:**
> My problem started one night. I was buying a Nintendo DS off Ebay, and everything went smoothly. I shut the computer down and turned it off at the mains.
When I tried to start it up the morning after it went through its grub routine and finally got round to starting Ubuntu. except it didn't. I was greeted with a message telling me that it had encountered error 2 and ubuntu was a unreadable file or directory. this signifies to me that ubuntu has become corrupted in some way or another... this is _***not***_ my real problem.

I need to assess my old home folder and retrieve my documents. I am currently working on copy of fedora that I used formerly. some time in the past, when install a program of some kind, I was instructed to use a command line that let me assess all folders with the power to change any of the properties. I have the root password for both systems, I just need to find a way to utilise this asset. think of it like having a bike but being told you can only walk.

anyway... this is a matter of importance to me.. also, if anyone could tell me why Ubuntu failed I would appreciate it as I have been told if ubuntu is not made stable windows xp will replace it....

Well the very first thing that I would want to do is to get the diagnostic software provided by the manufacturer of my brand of hard drive and see if there were any hardware problems with the drive.

---

### Post by laurielegit on 2008-07-18
> **bumanie said:**
> As for graphical superuser mode in fedora - I think it is  - Fedora uses gnome like ubuntu, so I assume the file manager is nautilus. gksu should give graphical superuser mode. Ever need the same function in ubuntu gksudo nautilus

that failed but I think the fedora forums may be able to help... I just thought this would be the best place as it has always been so helpful.

---

### Post by bumanie on 2008-07-18
> **laurielegit said:**
> that failed but I think the fedora forums may be able to help... I just thought this would be the best place as it has always been so helpful.Probably, I've not used fedora. You could try to retrieve your data via a live cd or you could try dd commands to copy the data to another drive/partition.

---

### Post by Titan8990 on 2008-07-18
In fedora you need to log in an root. I have found that by default you can sudo next to nothing. Being able to sudo almost everything is a trait of the debian base distros.

---


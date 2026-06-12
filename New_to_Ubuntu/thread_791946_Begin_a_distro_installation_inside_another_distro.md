---
title: "Begin a distro installation inside another distro?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by darrelljon on 2008-05-12
How can I begin a distro installation whilst using another Linux distro. I understand in Windows to just click setup.exe but how do I do it in a non-Windows OS, when for example the CD won't boot but can still be read from.

---

### Post by barney385 on 2008-05-12
I think you can use VMware.
 
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
 
edit: Check the repo's first!!

---

### Post by ZabiGG on 2008-05-12
The most pain-free way is to do it in Virtual Box (you'll find it in Add/remove applications if it's not installed already).

It will create a virtual disk where you can "install" your distro disk image (from an ISO CD image)

their site (for installation info): [http://www.virtualbox.org/](http://www.virtualbox.org/) 

It's fast and easy, even for the newbie that I am ;)

Cheers,

Zabigg

---

### Post by barney385 on 2008-05-12
> **ZabiGG said:**
> The most pain-free way is to do it in Virtual Box (you'll find it in Add/remove applications if it's not installed already).
 
It will create a virtual disk where you can "install" your distro disk image (from an ISO CD image)
 
their site (for installation info): [http://www.virtualbox.org/](http://www.virtualbox.org/) 
 
It's fast and easy, even for the newbie that I am ;)
 
Cheers,
 
Zabigg
 
Yes, that's the one I was thinking of...
 
:lolflag:

---

### Post by darrelljon on 2008-05-13
I'm not thinking of virtualisation as much as replacing e.g. in the same way, one might install Windows XP over an existing Windows 98.

---

### Post by Tatty on 2008-05-13
> **darrelljon said:**
> I'm not thinking of virtualisation as much as replacing e.g. in the same way, one might install Windows XP over an existing Windows 98.

In that case you would typically burn an installation CD and then reboot your machine with the CD in the drive.  Your computer should then detect an OS on the CD and boot from it to begin installation.

---

### Post by ByteJuggler on 2008-05-13
> **darrelljon said:**
> I'm not thinking of virtualisation as much as replacing e.g. in the same way, one might install Windows XP over an existing Windows 98.

To add to what the other posters have said, please note that if you are wanting to **upgrade** an existing linux installation (of another distribution of Linux) to Ubuntu, e.g. retain configuration/applications: You can't, at least not automatically.  There's far too many differences/unknowns between various distro's to make that practical in general.  

In order to more or less achieve what you want (e.g end up with an Ubuntu system with similar software/configuration and the same data from your other Linux install), you would have to backup the data and configuration items you want to keep manually, then do a clean reinstall from a LiveCD, followed by restoring data/installing the equivalent packages you had on the old installation.

---


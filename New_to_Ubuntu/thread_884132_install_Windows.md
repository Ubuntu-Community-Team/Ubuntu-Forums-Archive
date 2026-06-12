---
title: "install Windows"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by EvlZrglng on 2008-08-08
Hey i am currently running Ubuntu and want to know how to uninstall it to get Windows XP.  I do not need any of the data and have the XP disc.  I dont know anything about computer software :(  Help is much appreciated.

Evlzrgln

---

### Post by st33med on 2008-08-08
Install Windows XP by popping the disc in. Now, this will override your GRUB menu, so, once you have installed XP boot into the Ubuntu LIVECD and do this in the terminal:
```
sudo mount /dev/sda1
sudo grub
```

Replace /sda1 with whatever partition number it was on.
[Follow this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after you start grub.

---

### Post by cdtech on 2008-08-08
Use the "Live CD gparted" to remove partitions and reformat to vfat. Then boot with the XP disc and select to use the entire disk for the XP install.

---

### Post by bobnutfield on 2008-08-08
You don't need to do anything except insert your XP install cd into your drive, begin the install process, and when asked, allow Xp to format your entire drive.  Ubuntu will be gone and XP will be installed.

---

### Post by EvlZrglng on 2008-08-08
i try but after it installs it says starting windows i get the BSOD...

---

### Post by Thingymebob on 2008-08-08
> **EvlZrglng said:**
> i try but after it installs it says starting windows i get the BSOD...

Welcome to windows!

---

### Post by bobnutfield on 2008-08-08
> **EvlZrglng said:**
> i try but after it installs it says starting windows i get the BSOD...

I do not believe that has anything to do with your previous Ubuntu installation.  But, to be certain, if you have a copy of Partition Magic available, simply reformat your entire drive as NTFS, then try to reinstall Windows.  If you continue to get the BSOD, your Windows disc may be damaged and causing some files not to be installed correctly.  This has happened to me in the past as well.

---

### Post by OffAxis on 2008-08-08
The ultimate boot cd also has a number of utilities to erase and reformat drives.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by EvlZrglng on 2008-08-08
i get a 0x0000007B error when it says starting windows during the installation

---

### Post by OffAxis on 2008-08-08
Here's the official word from microsoft on that error:
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---


---
title: "Rocketfish External (Enclosure) HDD Unrecognized by Windows"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Faradin on 2008-08-11
So my laptop's mobo was fried about a month ago; I just got my PC back, which runs Vista. I bought a Rocketfish brand SATA Hard Drive enclosure to back up my laptop's HDD (running Ubuntu) onto my PC, but once the device was installed and the driver downloaded, the SATA hard drive became unrecognizable. Help?

---

### Post by cozmicharlie on 2008-08-11
So did it become unrecognizable in your vista machine?  So the HD in the Rocketfish was the HD that came out of your laptop when it was fried - correct?  If you are trying to mount it in Vista it is most likely the files system is ext3 (default file system in Ubuntu) your vista box can't read ext3 file systems.  If so then you have a couple options.  Find another drive (ntfs) and transfer the files to it using a Linux computer.  There are programs you can install in XP that will let Windows read ext3 but I am not sure they work in Vista.  You also could install Virtual Box in Vista, load a Ubuntu install and transfer the files in Virtual Box.

---

### Post by bpowell2005 on 2008-08-11
> **cozmicharlie said:**
> So did it become unrecognizable in your vista machine?  So the HD in the Rocketfish was the HD that came out of your laptop when it was fried - correct?  If you are trying to mount it in Vista it is most likely the files system is ext3 (default file system in Ubuntu) your vista box can't read ext3 file systems.  If so then you have a couple options.  Find another drive (ntfs) and transfer the files to it using a Linux computer.  There are programs you can install in XP that will let Windows read ext3 but I am not sure they work in Vista.  You also could install Virtual Box in Vista, load a Ubuntu install and transfer the files in Virtual Box.

Agreed. I think you're trying to access an EXT3 drive with Windows which doesn't work (without 3rd party software). I think the suggestion of installing a virtual linux system is a great idea; create a shared drive on your windows machine, install a virtual linux system, grab data from the external drive and put it in the shared windows drive.

---

### Post by cariboo on 2008-08-12
Go here:

 [http://www.fs-driver.org/](http://www.fs-driver.org/)

for software to access your ext3 patitions from windows

Jim

---


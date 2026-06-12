---
title: "Is Linux on USB a bad idea?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-07-26
After many hours for trying to make this work I have tried ubuntu on 2 USBs. The first USB, which works fine in windows appears to have buffer errors of some sort. Even after multiple formats and reinstall the first USB (sandisk Cruser 1GB) it kept going to boot crashes where casper complained about File Not Found an I/O buffer errors. So I went out and bought another USB. This one ran well giving me the ability to change settings, ect. After about the 4th powerup it started giving me "gnome session manger was unable to lock the /home/ubuntu/.iceAuthority". It would then make some drum roll sound and ask for a user name and PW. I never set one up. 

Do USBs just not maintain data integrity? Or perhaps when ubuntu logs off it still processing something in the drive, even though it says it ok to pull out? I ran error checking and that didnt help. Live CD works great, but im too lazy to partition my HDD so I went with USB.

---

### Post by Bachstelze on 2008-07-26
What exactly do you want to do? Install Ubuntu without a CD, from an USB drive? If so, what kind of install?

---

### Post by Lateforgym on 2008-07-26
I want to do is have linux on a usb, where I can make changes to its settings, update and have changes save on it. That way if Windows corrupts, which I seem to pull off once a year, I can simply use the USB OS till I have time to fix windows. Live CD works great in 8.04 but there are little things like flashplay not being installed in firefox.

---

### Post by neurostu on 2008-07-26
Yes that is a great Idea... there is actually a utility to move a LiveCD onto a usb drive.

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by impert on 2008-07-26
> **Lateforgym said:**
> I want to do is have linux on a usb, where I can make changes to its settings, update and have changes save on it. That way if Windows corrupts, which I seem to pull off once a year, I can simply use the USB OS till I have time to fix windows. Live CD works great in 8.04 but there are little things like flashplay not being installed in firefox.

Why not dual-boot?

---

### Post by billgoldberg on 2008-07-26
> **Lateforgym said:**
> I want to do is have linux on a usb, where I can make changes to its settings, update and have changes save on it. That way if Windows corrupts, which I seem to pull off once a year, I can simply use the USB OS till I have time to fix windows. Live CD works great in 8.04 but there are little things like flashplay not being installed in firefox.

They are working on a usb installer for Ubuntu 8.10, that comes out in a few months.

Also, there are distro's like damn small linux that will run better on a usb pendrive.

---

### Post by bumanie on 2008-07-26
Pendrive linux (2 posts above) has never failed for me if done within ubuntu - I did have probelms when I tried to do it from within windows. Look at the above site, there are various methods available.

---

### Post by linuxrus1 on 2008-07-28
[QUOTE=Lateforgym;5462195]After about the 4th powerup it started giving me "gnome session manger was unable to lock the /home/ubuntu/.iceAuthority". It would then make some drum roll sound and ask for a user name and PW. I never set one up. 

I saw this too.

I played around with deleting the .ICEauthority named files under ubuntu folder.
But I could not delete the .ICEauthority-c file.
So I renamed the file .ICEaut and the USB boot from USB thumb drive appears to work again.

I'm curious to find out who generates the .ICEauthority-c file.
The .ICEauthority file appears to get regenerated when missing.

---

### Post by kansasnoob on 2008-07-28
I'm somewhat unsure what you want, but I'll share this with you.

I have never tried installing Ubuntu to a flash drive, pen drive, etc. I have however purchased a Puppy Linux "thumb drive" here:

[http://www.linuxcdshop.com/linux/Puppy-Linux-USB-4-0-0.html](http://www.linuxcdshop.com/linux/Puppy-Linux-USB-4-0-0.html)

I use it to boot otherwise unbootable systems, but I don't care for Puppy as a desktop solution.

I have however installed Ubuntu to external hard drives, particularly from laptops. Of course I'm always prepared to deal with GRUB wiping out the laptops MBR, etc. (My preferred method of dealing with that situation is creating a separate GRUB partition on the mounted drive).

---

### Post by Zimmer on 2008-07-28
Best idea is to have Linux on a stick but use a cheat code to load it into ram. One I have tried and still use is MCNLive . Have partitioned the USB stick to have a data partition as well as the MCNLive bootable Linux.
I can then use the cheatcode copy2ram at boot time. Once the OS is in RAM there is no I/O and writing to the USB stick by the Operating System during use except for any files saved to the data  partition.
This will also extend the life of the USB flash memory.
MCNLive also has a remaster option which allows you to customise and install/uninstall apps and create your own personal ISO.

Knoppix also has  similar options coupled with a persistence option although I do recall seeing the odd Filesystem errors when last booting that one..

---


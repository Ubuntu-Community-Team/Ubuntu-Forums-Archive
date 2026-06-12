---
title: "[SOLVED] Installing Ubuntu Server"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Skivache on 2008-09-18
I have an older Dell Latitude notebook I would like to install ubuntu server on, but it doesn't have a cd-rom drive.  I have tried using UNetbootin to make a bootable USB drive, but the installation fails on the "Detect and mount CD-ROM" step.

I would like to know if there is any other way to install ubuntu server that doesn't involve a cd.  I do not want to run the installer on another machine as I want all the hardware to be detected in the original laptop.

Thanks for the help.

---

### Post by Skivache on 2008-09-19
I found this guide for installing ubuntu from a usb drive.[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

When I run these commands:
```
#
mkdir /cdrom /dev/cdroms
#
cd /dev/cdroms
#
ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
#
mount -t vfat /dev/cdroms/cdrom0 /cdrom
or
mount -t vfat /dev/hda3 /cdrom
```

I get a message saying 
```
vfat not found in file /etc/fstab
```

What can I do to make this work?

---

### Post by Sef on 2008-09-19
Did you follow these [directions]("https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html")?

---

### Post by Skivache on 2008-09-22
Yes, I did follow the instructions on making the flash bootable and did copy all the files.  It turns out I needed to add a line to the fstab file about how to open/mount the filesystem.

Now im running ubuntu server :guitar:

---


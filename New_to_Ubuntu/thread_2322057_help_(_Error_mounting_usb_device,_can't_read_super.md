---
title: "help :( Error mounting usb device, can't read superblock ?¿"
date: 2016-04-26
forum: New to Ubuntu
---

### Post by Marian_K. on 2016-04-26
Hi, i have a USB stick with some important documents, but when I try to use appears this:

Error mounting /dev/sdc1 at /media/kize/MAOA: Command-line `mount -t "vfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,shortname=mixed,utf8=1,showexec,flush" "/dev/sdc1" "/media//kize/MAOA"' exited with non-zero exit status 32: mount: /dev/sdc1 is write-protected, mounting read-only
mount: /dev/sdc1: can't read superblock

I would appreciate help me'm still new to ubuntu though I have months using this OS but I'm just casual internet user and office work.

tnx :)

---

### Post by leunam12 on 2016-04-26
First things first: if the USB stick was used in a Windows computer and wasn't properly ejected it usually creates problems when trying to use it in a Linux box; if this is the case, insert the stick on the Windows computer again and go to the lower-right corner of the screen to the utility that allows you to eject it safely.

[http://windows.microsoft.com/en-us/windows7/safely-remove-devices-from-your-computer](http://windows.microsoft.com/en-us/windows7/safely-remove-devices-from-your-computer)

---

### Post by Marian_K. on 2016-04-26
Windows recognizes that it is a usb kingston, but you can not see the memory on my pc or devices.

---

### Post by bob--treat on 2016-04-26
In Windows can you check the stick for errors? You say it can't see what's on the disk but is it showing mounted in Explorer? For this, let's call it E: Open a command prompt (Windows 10, type cmd in search next to start button, others Start/ search cmd.) A console opens with a prompt, if the drive is E: then type,    chkdsk E: /f   ,at the prompt, see what it does.

---

### Post by Marian_K. on 2016-04-26
hi, i can not see the device in Explorer, I can only be detected in the device manager . the browser does not show me anything, just my own hard drives.

---

### Post by bob--treat on 2016-04-26
The link ( [http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter](http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter) ) explains how you *may* run a chkdsk in Windows where you do not have a mount point. I'm inclined to say your problem lies with the USB device and definitely not Ubuntu. If you can get the check done and it mounts either in Windows or Ubuntu, copy the drive's contents into a folder as it is probably almost or dead.

---


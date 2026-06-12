---
title: "[SOLVED] Acessing USB external drive ?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Drakkor on 2008-08-25
I want to transfer some files from an external USB drive,but Ubuntu doesn't see or recognize the drive ! Any ideas ? Thanks :)

---

### Post by LowSky on 2008-08-25
is it plugged in and turned on....j/k

is it formated to NTFS (Windows XP) 
go to add/remove
search NTFS, install the NTFS config or whatever its called

it will be installed under Applications>System
check the boxes to automount and read write access, and you should be good to go

if that doesn't work, try to see if gparted can format if it has not been done so already.

---

### Post by Drakkor on 2008-08-25
None of that works,and yes it's NTFS, and I don't have NTFS in Add/Remove programs,and I don't want to format it, I want to tranfer files from it.

---

### Post by Drakkor on 2008-08-25
Somebody,please help me, I need to transfer the files from my external USB drive !! :(

---

### Post by Crafty Kisses on 2008-08-25
Post the results of this command > lsusb

---

### Post by pyromanic123boom on 2008-08-25
If it's NTFS, use the NTFS configuration tool.

add remove programs -> search : ntfs ->select NTFS Configuration Tool

---

### Post by pyromanic123boom on 2008-08-25
Sorry, read you don't have it in add/remove. Just follow this. Worked charms for me. 

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Drakkor on 2008-08-25
@Codeman

drakkor@drakkor-desktop:~$ lsusb
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 04ca:0020 Lite-On Technology Corp. 
Bus 001 Device 007: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 006: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 001 Device 001: ID 0000:0000  
drakkor@drakkor-desktop:~$

---

### Post by Drakkor on 2008-08-25
And the only thing I get with the NTFS configuration tool is this:

---

### Post by pyromanic123boom on 2008-08-25
So once you check the box, does it work?
It's just telling you that there's an external ntfs drive and no internal ntfs drive.

---

### Post by Drakkor on 2008-08-25
I don't really know,since it doesn't show up anywhere,as far as I can see

---

### Post by kansasnoob on 2008-08-25
Well, two things:

(1)To be sure you can read ntfs install ntfs-config either from syanptic (safest way) or:

```
sudo apt-get install ntfs-config
```

(2)Try either usbmount or psbmount (which depends on hal). again you can install either from syanptic or cli, to auto-mount your external drive.

---

### Post by kansasnoob on 2008-08-25
> **kansasnoob said:**
> Well, two things:

(1)To be sure you can read ntfs install ntfs-config either from syanptic (safest way) or:

```
sudo apt-get install ntfs-config
```

(2)Try either usbmount or psbmount (which depends on hal). again you can install either from syanptic or cli, to auto-mount your external drive.

Oops! Psbmount should be pmount!

---

### Post by Drakkor on 2008-08-25
Yeah,I already have ntfs-config, and installed pmount,but still can't see the drive ! :(

---

### Post by pyromanic123boom on 2008-08-25
What type of drive is it, exactly?
go into Places-->Computer and see if it isn't there, waiting to be mounted.

---

### Post by Drakkor on 2008-08-25
I'm a certified idiot !!!   :redface:
I had it all hooked up with the exception of the USB cord into the computer.
now it's right there. It's always the simple things we overlook,I guess. Thanks to  all who replied :)

---

### Post by Drakkor on 2008-08-25
How do I mark this as Solved ?

---


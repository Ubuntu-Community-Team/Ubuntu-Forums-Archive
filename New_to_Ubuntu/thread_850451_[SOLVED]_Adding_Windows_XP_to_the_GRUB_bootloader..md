---
title: "[SOLVED] Adding Windows XP to the GRUB bootloader."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-07-05
Somehow, during my Ubuntu install, Windows didn't get recognised, and the bootloader doesn't have a Windows boot option now. How do I add a new option to the bootloader so I can boot Windows?

sudo fdisk -l gives me:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091178

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2           26747       27791     8388608   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3           27791       30402    20971520    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            2433       26746   195302205   83  Linux

Partition table entries are not in disk order

---

### Post by TeoBigusGeekus on 2008-07-05
```
sudo gedit /boot/grub/menu.lst
```
Add these lines at the end of the file
```
title		Window$ XP
root		(hd0,2)
makeactive
chainloader	+1
```
Don't forget to post us what happened.

---

### Post by Madman6510 on 2008-07-05
It added windows to the bootloader, but when I select it, windows moans:

Starting up...

NTLDR not found
Press CTRL+ALT+DEL to restart.

---

### Post by sayakb on 2008-07-05
NTLDR is a file located in the windows drive. You might have removed it somehow.
[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)

---

### Post by TeoBigusGeekus on 2008-07-05
See if these pages are of any help
[http://support.microsoft.com/kb/555304]("http://support.microsoft.com/kb/555304")
[http:/http://www.computerhope.com/issues/ch000465.htm/]("http:/http://www.computerhope.com/issues/ch000465.htm/")

---

### Post by louieb on 2008-07-05
Prior to installing Ubuntu did the PC dual boot 2 versions of Windows (Win9x,me,XP,vista)?
Windows installs its boot loader in the older OS when the newer one is installed. (Don't know why).
IF you removed the older OS to install Ubuntu that would be why the window boot loader  ntldr is missing.  

pretty good decription of the fix here.[http://www.bestpricecomputers.ltd.uk/freehelp/ntldr_missing.htm](http://www.bestpricecomputers.ltd.uk/freehelp/ntldr_missing.htm)

---

### Post by Madman6510 on 2008-07-05
Fixed it by adding in a replacement NTLDR file, and editing it with a "personal touch".

---


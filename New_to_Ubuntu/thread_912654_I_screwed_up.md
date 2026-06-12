---
title: "I screwed up"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by garrettstarnes on 2008-09-06
OK guys.  I screwed up this time.  I don't know how I did it, but I did.  I tried to install xubuntu on my thumbdrive.  I did, I think.  Here's the deal.  If I boot up my computer with my thumbdrive in, I can choose at bootup between windows vista, ubuntu, or xubuntu (also labeled ubuntu, but whatever).  If I remove the thumbdrive and try to boot.  I get this:

    Grub loading stage 1.5
    Grub loading, please wait
    error 21

If I put the thumbdrive in and reboot.  I can get to the screen that lets you choose the OS.  If I take the thumbdrive out at this point and select an OS, I get this:

    Error 25: disk read error
    Press any key to continue

Then it takes me to the previous screen (choose an OS)

I think somehow I lost the Grub on my hard disk and have it on my thumbdrive.  Everything works fine if the thumbdrive is in, but it won't work without it.  Someone please tell me you know how to fix this!!  I am fairly new at linux (as is apparent) and would appreciate any help.

Thanx!!

---

### Post by rossjman1 on 2008-09-06
You installed Xubuntu on your thumb drive, so you would need it plugged into your computer for it to work...
[edit]Sorry, misunderstood your post.

---

### Post by OutOfReach on 2008-09-06
Basically, GRUB looks for the thumbdrive..Ok the thumbdrive isn't plugged in, GRUB gives an error 21 (Meaning an absent partition/disk).
So I would suggest removing the Xubuntu entry from the GRUB menu...Or plugging in your thumbdrive everytime you boot

---

### Post by gletob on 2008-09-06
Google is your friend
[http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)
And this is the guide to install it (for ubuntu but xubuntu should work the same way)
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

---

### Post by garrettstarnes on 2008-09-06
That link seems very helpful, just one question though.  I did the fdisk -l thing, and this is what I got:
    Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313        9843    68519531+   7  HPFS/NTFS
/dev/sda4            9844       14593    38154375    5  Extended
/dev/sda5   *        9844       14392    36539811   83  Linux
/dev/sda6           14393       14593     1614501   82  Linux swap / Solaris

Disk /dev/sdb: 2047 MB, 2047678976 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044bff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         230     1847443+  83  Linux
/dev/sdb2             231         248      144585    5  Extended
/dev/sdb5             231         248      144553+  82  Linux swap / Solaris
root@StarnesFamilyLaptop:/home/user# 

Call me an idiot, but which one is my linux boot partition?  I just don't want to screw up in root.

Thanx!

---

### Post by garrettstarnes on 2008-09-07
gletob....you saved my life. If you lived in South Carolina, I would have my wife make you some fried chicken.  It's pretty good.  Really.

Thank you!!
SOLVED

---

### Post by gletob on 2008-09-07
Southern Fried Chicken? thats almost worth flying from VA for :lolflag: ( my wife refuses to fry chicken)
Your welcome for the help and I'm glad to help

---


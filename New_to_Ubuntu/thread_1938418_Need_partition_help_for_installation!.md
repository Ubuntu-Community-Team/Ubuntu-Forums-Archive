---
title: "Need partition help for installation!"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by fluffy283 on 2012-03-09
I cant seem to install Xubuntu 11.10 where or how I would like. Ideally I would install it on my external hard drive which has over 200 GBs of open space. I also have a 19 GB partition on my C drive. I want to dual boot but the CD installation wants to install onto my external hard drive and take up all of the 200+ GBs of space. It lets me change which partition gets how much space but I cant lower the amount of space the entire install will use. And if that's not bad enough, it doesn't even let me change to my 19 GB partition.

I wanted a portable Xubuntu hence the USB hard drive but there's no way I'm letting Xubuntu have all that space. Please help.

---

### Post by kikotiger on 2012-03-09
What option did you selected when it asked you where you wanted to install the OS?

---

### Post by fluffy283 on 2012-03-09
I chose to install alongside Windows [I have XP Professional SP3] because I'm not familiar enough with Linux for it to be my only system and I have too much stuff on my Windows to lose. I also can't get Ubuntu to see my internet device so I wouldn't be able to update it or download any updates or packages or anything.

After I chose install alongside Windows, it went to the part where you slide the bar to choose your partitions. That's the part where it tried to use my entire USB drive. I clicked on Choose Drive at the top but it didn't give me any other options except that drive, so I quit the installation.

A little bit ago I tried installing to the USB hard drive via Wubi and allocated 25 GBs. Right at the end it said that the installation was unsuccesful and something about permission denied then gave me some long file path where the log is located and I can't find it >.< I have no idea why it would say permission denied, I'm the only user on this computer and I'm an administrator account.

---

### Post by oldfred on 2012-03-09
If you choose along side, it will probably be installing to your internal drive. You need to use manual install and also be sure to install the grub2 boot loader to the MBR of the external drive. Then in BIOS set to boot external first.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by fluffy283 on 2012-03-09
Okay, thank you for the links, I will read those asap and get back to you when I have had a chance to try your instructions :)

---

### Post by ajgreeny on 2012-03-09
Choose "**Something Else**" at the disk preparation stage (partitioning), and your external drive will appear in the available disk/partition options.  You will also need to make sure that you install the bootloader files to the external disk (probably dev/sdb) or you will be unable to boot windows when the external drive is not attached.

---

### Post by fluffy283 on 2012-03-21
Okay so I ended up going with install alongside windows and it seemed to go just fine, until reboot... I assume the screen I found myself staring at after choosing Xubuntu is the "grub bootloader". It says something about minimal bash like editing or something and below that the command input just says "grub>". Intimidating. I decided to try a partitioned install again and got slightly better results. I now get a partition display that has (I might get this wrong) /dev/sda and /dev/sdb as well as sdb1 that says it's NTFS. But the add button is grayed out on both sdb and sdb1 so I'm not sure how to proceed. I quit the installer to avoid any mistakes

---

### Post by oldfred on 2012-03-22
If you said along side it installed to your internal drive. Your external is sdb1 and still is NTFS not Linux.

Post this from liveCD:

```
sudo fdisk -lu
```

A grub> is an error where some part of grub is not found. 

You cannot install Ubuntu to NTFS unless you use wubi. Best to create Linux partitions and install to those.

---

### Post by fluffy283 on 2012-03-22
OK do you want me to post that on the grub> screen or do you want me to use demo mode and post that in the terminal?

---

### Post by oldfred on 2012-03-22
The grub> command cannot run much, it is not a full terminal. Just use liveCD.

It may be easier to download and run this in the liveCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---


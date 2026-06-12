---
title: "Fatal Error 'grub-install' failed"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by DDurcsak on 2008-08-17
Ubuntu Forum:

During the last part of the OS installation I receive a Fatal Error

Executing 'grub-install(hd0)' failed.

Should I be looking to install 'grub" at another point...there was a drop down list of locations??

Thank you

---

### Post by nicedude on 2008-08-17
Grub normally installs the begining of its code to your disks MBR and the rest to your Ubuntu EXT3 partition in a directory called /boot/grub/

Do you have more than one hard drive in this PC or any USB disks etc plugged in ? (hd0) setting works for me when installing to a single drive just fine but can cause problems with multiple disks ( or has for me before ).

---

### Post by Bucky Ball on 2008-08-17
Don't mean to be the angel of doom, but was that hard drive working before the install? No a hardware problem?

---

### Post by ace007 on 2008-08-17
I've had this problem too.  I got it to work after a few more attempts.  I want to say I was attempting to install on the wrong hard drive? Or maybe the hard drive was in the wrong channel? 

Sorry, I think the problem worked itself out.  But i can confirm that this happened to me too.

---

### Post by DDurcsak on 2008-08-18
> **nicedude said:**
> Grub normally installs the begining of its code to your disks MBR and the rest to your Ubuntu EXT3 partition in a directory called /boot/grub/

Do you have more than one hard drive in this PC or any USB disks etc plugged in ? (hd0) setting works for me when installing to a single drive just fine but can cause problems with multiple disks ( or has for me before ).

I do have another hard drive.  Both are in working order.

I was wondering if I should have chosen another of the options in the drop down list of install points for 'grub'??

/dev/sda (primary HD with partitioned for both WIN and Ubuntu)
/dev/sda1 MS WIN XP
/dev/sda2
/dev/sdb (Secondary drive partitioned for WIN data and Ubuntu Swap)
/dev/sdb5

---

### Post by nicedude on 2008-08-18
Yes I believe you should choose /dev/sda and it will work. This sort of thing only happens when there are more than one physical hard drive in the PC. A good idea sometimes when doing installs is to either unplug the drive you won't be installing to or disable it in the BIOS if that is easier, that way you rule out any such problems from occurring. You don't have to do that but it just makes installs easier sometimes ( heck I even do it if installing Windows sometimes if there are say 4 or 5 hard drives in a box, just so I know I get the drive I want )

Also I don't know if you will see any benefit from having your SWAP on another physical drive. But keep in mind that if you ever remove that drive then Ubuntu wont boot until you make it a new SWAP. Just thought you should know that as well.

I would start off by undoing whatever partitions you made with the Ubuntu install disk and then reboot ( so the disks partition tables will update ) and now reinstall Ubuntu and use the /dev/sda for grub :-) this should work.

If you get it going don't forget to post here that you did so, and mark this thread as SOLVED so others will know you got it working and not try to keep answering you.

PS And don't worry about anything being wrong with your disk physically as that was not your problem. ( Always a good thing when problems dont take money to solve :-) )

Hope all this helps you figure it out :-)

Goodluck, I will check back later to make sure you got it working.

---

### Post by DDurcsak on 2008-08-18
To all:

Just got a response from CalJohnSmith.

Bottom line is it worked and was very simple:

I've heard that is a bug that can be circumvented by formatting the Ubuntu partition to ext2 instead of ext3 when you install Ubuntu. Try that, and if it works you can later "ugrade" your file system to ext3 with:
Code:

sudo tune2fs -j /dev/sdXY

Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2".

---

### Post by Bucky Ball on 2008-08-19
Maybe go here, burn a copy and boot from it before you get extremely involved. If it fixes, Great! By the looks of your install which you posted above, it is all there and this would probably fix.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---


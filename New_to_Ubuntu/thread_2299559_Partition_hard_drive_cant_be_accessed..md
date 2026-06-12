---
title: "Partition hard drive cant be accessed."
date: 2015-10-19
forum: New to Ubuntu
---

### Post by Lucas_Winther on 2015-10-19
I have a partition hard drive with 400GB on it, but i cant acces it. I think its because i made it a partition, but how do i undo that and add space to my ubuntu OS?

OBS: EFI SYSTEM

---

### Post by v3.xx on 2015-10-19
The two places I go to for instruction.

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Lucas_Winther on 2015-10-19
Thank you for the answer. But there is a problem. The 400GB hard drive is located at /

When i try to unmount/resieze the disk, it tells me the following: " The partition could not be unmounted from the following mount points:   /   most likely other partitions are mounted on these mount points. You are advised to unmount them manually. Now as i see it, the only other path at / is /boot, which is the system. Have i messed up BIG time? I will do anything to make the hard drive my main. Cause 4GB is not enough.

---

### Post by v3.xx on 2015-10-19
Can you post a snapshot of your partitioning?

---

### Post by Lucas_Winther on 2015-10-19
Yes certainly - [http://tinypic.com/r/2zsv4t1/8](http://tinypic.com/r/2zsv4t1/8)

---

### Post by v3.xx on 2015-10-19
This looks pretty straight forward to me, but..

I do not run efi so I will have to decline on giving further instructions that may or may not work for your filesystem.

I would suggest editing your thread title to include EFI.

Good luck

---

### Post by Lucas_Winther on 2015-10-19
Thank you, thanks for taking the time to try to help me :D

---

### Post by buzzingrobot on 2015-10-19
Gparted is on the Ubuntu live install image.  You could boot from that, run it in the "Try" mode, use gparted and deal with those partitions. 

I believe Ubuntu's installer will create any /boot/efi partition it needs on a UEFI machine, but I don't have UEFI hardware so that needs to be verified.

---

### Post by buzzingrobot on 2015-10-19
BTW, are you trying to reduce the size of that Linux partition to create space for Windows to use?

---

### Post by yancek on 2015-10-19
In your initial post you indicate that you want to add space to your Ubuntu OS.  The only Linux filesystem partition is the 460+GB partition listed as root which is the only place Ubuntu could be.  Maybe stating what your end goal is would help.  The only other partitions you have are the EFI partition and swap which are very small.  So if you are booting to Ubuntu, you are accessing it.

---

### Post by Geoffrey_Arndt on 2015-10-19
From the screenshot, it seems you have one hard drive (sda) with 3 partitions on it:  a boot, a main with all of ubuntu system and user files on it, and a swap.   You have a small (insignificant) amount of unallocated space).

So, if you see Ubuntu load up upon startup, it appears to be your only OS.   _That main partition **(sda2) is being accessed** if it brings up Ubuntu_.   Do you have a second hard drive (like sdb)?   From the ubuntu file manager (nautilus), you should be able to access all those files and folders, and the normal default screens you see are you user home folders (/home).

BTW, your opening post wording makes no sense at all from a technical perspective.   All data (directories/folders and files) are located inside partitions.   All partitions are accessible from the Linux OS.   Windows OS will only see other Windows partitions (a partition with a windows file system on it - like fat32 or ntfs).

---

### Post by Lucas_Winther on 2015-10-20
Thank you guys. I am just a technical failure. I realised that what i wanted to have is what i already have. Thanks for all the answers, and sorry to have wasted your time(To say, i thought i had 400 MB left when i checked, but in reality it was 400GB(i know im dumb))

---

### Post by Geoffrey_Arndt on 2015-10-20
Don't get too down on yourself Lucas . . . just trying to install Linux shows promise of better things to come.   At least you're trying, and you'll learn a little more each day.   The forums here, AskUbuntu, and many other sites (including YouTube) can be very helpful.   Stay positive, you have friends here!

---


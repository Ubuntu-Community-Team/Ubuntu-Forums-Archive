---
title: "Dual Boot Partitioning Help Needed"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by /newbie on 2011-12-29
I was attempting to do a dual-boot with ubuntu 11.10 and windows 7 (which is already installed). While working with the installation's partitioning editor, I accidentally made some sort of mistake and created a 200gb "unusable" partition. I did this by selecting the sda2 partition (where windows 7 is installed) and selecting "change...". From there I resized the partition, but I had "do not use the partition" selected when I resized it. I am now stuck with this 200gb of unusable space and I do not know how to fix it.


How would I convert the "unusable" space into separate usable partitions so that I can complete the ubuntu installation? Also, will I need to make a swap partition, or will the installation make one automatically?

So far this is how the hard drive is partitioned:

[IMG]http://s8.postimage.org/rqkxk49vp/Screenshot_at_2011_12_30_01_14_47.png[/IMG]


Any help would be greatly appreciated. 

Thanks!

---

### Post by Basher101 on 2011-12-29
Looks like you just shrunk down your windows partition and now you have 200gb of unallocated space. Cancel the installation and open up Gparted to give that unallocated space a filesytem (e.g. ext4 for a dualboot). That should be enough space for the installer to give you the option "Install next to windows" which will handle mounting points, swap space and bootloader automatically..

---

### Post by /newbie on 2011-12-29
I just found out that the computer (an HP laptop) is limited to only 4 partitions.

 I deleted one of the partitions I did not need and the space became "free" and I was able to make a 200gb ext4 partition as sda4.

 Now I have another problem . . . How to I make a swap partition if I don't want to delete sda1, sda2 and sda3?

Do I need to make a "logical" partition from sda4?

Will the ubuntu installation automatically do this if I select "install" on sda4?

---

### Post by critin on 2011-12-29
Hey Newbie...
I would suggest looking at a few tutorials about partitioning before messing with yours too  much.  You're lucky you didn't lose your Windows.  :P 

Good luck and enjoy learning.

---

### Post by critin on 2011-12-29
> **/newbie said:**
> I just found out that the computer (an HP laptop) is limited to only 4 partitions.

 I deleted one of the partitions I did not need and the space became "free" and I was able to make a 200gb ext4 partition as sda4.

 Now I have another problem . . . How to I make a swap partition if I don't want to delete sda1, sda2 and sda3?

Do I need to make a "logical" partition from sda4?
[B]
Will the ubuntu installation automatically do this if I select "install" on sda4?[/B]

Yes, it will do it automatically.  I'm wondering which partition you didn't 'need'.  :confused:

---

### Post by /newbie on 2011-12-30
HedgeHog1's way worked
[http://ubuntuforums.org/showthread.php?t=1725956](http://ubuntuforums.org/showthread.php?t=1725956)

---


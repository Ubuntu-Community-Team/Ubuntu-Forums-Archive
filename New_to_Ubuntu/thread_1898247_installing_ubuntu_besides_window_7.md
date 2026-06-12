---
title: "installing ubuntu besides window 7 ?????"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by akdekk on 2011-12-20
Hi all,
I'm an absolute beginner to linux.
I've already installed ubuntu to my mom's laptop as an experiment :P
But I'm having a problem of installing it on my laptop HP dv7.
I want to keep my window 7 and have linux aside, because I like this Blu ray player feature on the window 7. that is the only reason. If you know any way to play Blu ray on linux, please educate me.

So my problem is that there is no option for installing ubuntu in a space other that window 7 or whatever that the guide of installation says.
Then I tried to do something else with partition. But I didn't have any free space, so I shrank one and made 22GB of free space. However, it was unallocated, unusable it says. So I formatted and it became usable, BUT! it doesn't show on the installation!
I don't know what to do....T T

Please help.
I want to use LINUX!!
Thanks.
Merry Christmas and Happy holiday!

---

### Post by alphacrucis2 on 2011-12-21
> **akdekk said:**
> Hi all,
I'm an absolute beginner to linux.
I've already installed ubuntu to my mom's laptop as an experiment :P
But I'm having a problem of installing it on my laptop HP dv7.
I want to keep my window 7 and have linux aside, because I like this Blu ray player feature on the window 7. that is the only reason. If you know any way to play Blu ray on linux, please educate me.

So my problem is that there is no option for installing ubuntu in a space other that window 7 or whatever that the guide of installation says.
Then I tried to do something else with partition. But I didn't have any free space, so I shrank one and made 22GB of free space. However, it was unallocated, unusable it says. So I formatted and it became usable, BUT! it doesn't show on the installation!
I don't know what to do....T T

Please help.
I want to use LINUX!!
Thanks.
Merry Christmas and Happy holiday!

You probably formatted the free space as NTFS or FAT32 which is of no use to the Ubuntu installer. 

Just leave the free space as free space.

---

### Post by akdekk on 2011-12-21
Thanks for the reply! ^^
well, at first I didn't formatted it.
after shrinking, it said unallocated. I booted with ubuntu CD again, and it did say free space but it also said unusable and I couldn't go forward..

---

### Post by Miljet on 2011-12-21
How many partitions do you have?

---

### Post by akdekk on 2011-12-21
I have 4; system, C, recovery, HP tools.
I just undid format the one free space and did single new volume, and it became RAW... OMGoodness

---

### Post by Miljet on 2011-12-21
You can only have 4 primary partitions, so you have to decide which of the existing partitions you want to delete. Then you can make that deleted partition into an extended partition, which can contain numerous logical partitions.

Here is more info.  [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by akdekk on 2011-12-21
Don't I need those 4 partitions? I have no clue of what to delete... T T

---

### Post by mastablasta on 2011-12-21
Backup HP tools and delete it. you do not need it probably.
 
yoou can create an image of it (exact same copy of partition bit-by-bit) if you wish to an external drive, usb key etc.

---


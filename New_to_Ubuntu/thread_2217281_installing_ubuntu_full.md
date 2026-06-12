---
title: "installing ubuntu full"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by james120 on 2014-04-16
After trying ubuntu 12.04 lts for awhile and being totally new to linux I've decided to install the full version extended flavor.  Now it's installed using the wubi install which I will delete using revo uninstaller.  I really can't decide if to partition my hard drive using easeus partition or windows disk utility or allowing the ubuntu install do it.  Which would you think would be better?  Now I'm using the 64bit version of ubuntu to take advantage of the additional ram. Installed ram is 4gb.  I've got xp home 32bit version installed on a 1tb hdd.  Would it be ok to use the 64bit version? It seems to run ok now. I want to make it dual boot as it is now. Will I need to make the root a primary partition or or will the iso file do that for me?   Is the swap file installed on it's own partition?  Will the downloaded iso file do this?  Will The other partitions be a logical partition.   Also will the iso image fit on a cd or do I need to use a dvd.  I'll burn it using imageburn.  I'm going to slice it as follows: 300gb total.  How much do I need for the swap file?  I'm not going to hibernate though, only use screen saver. It's a desktop computer.  How much for the root?  I know the rest will be used for the home folder.   In total will there be 3 partitions?  My present setup is c:\ for windows.  D:\ for an internal hdd, then E and F for the two cd/dvd roms/writers.  Thanks

---

### Post by jbaerboc on 2014-04-16
Hi James, if you're going to install Ubuntu LTS I would suggest waiting for the final release of 14.04 LTS. This will provide many improvements and updates over 12.04 LTS and give you a longer support windows that what's left on 12.04 LTS. The 14.04 LTS is going to be released on the 17th [so tomorrow]. I'm running the Beta and have been for 2 weeks now with no issues so I'd imagine the released version would be the same or better.

As far as who to let handle the partitioning I would recommend letting the Ubuntu installer handle it. The reason being that it is built specificaly with installing Ubuntu in mind. I haven't used Wubi before though so may be best to let someone else advise you on it. I typically try a LiveCD/DvD and then install from there.

---

### Post by Impavidus on 2014-04-16
That are a lot of questions.

Good that you want to move on from wubi to a real dual boot.

Use the Windows disk utility to defragment and shrink the Windows partition (C and/or D) to create unallocated disk space. If D is a logical partition, make sure the unallocated space is adjacent. Not entirely clear from your post whether you have two partitions on one drive or two drives. In the Ubuntu installer you can select "Install alongside Windows" and it will handle everything automatically. If you have multiple drives or want more control (such as when you want a separate /home partition), go for something else (manual partitioning). You can specify the partitions using the installer or do it beforehand, using gparted, which is present on the live disk. Ubuntu doesn't care whether it is on a primary or logical partition. It seems you want root (aka /), /home and swap partitions.

32 bit Ubuntu can handle all your ram, but using 64 bit Ubuntu is better. It doesn't matter too much. The iso won't fit on a cd, so use a dvd or usb drive.

If you don't hibernate 2GB of swap should be enough. If you allocate 300GB to Ubuntu, you won't notice any difference when you make it a few GB larger though. About 20–30GB should be enough for your root partition, depending on what you want to do.

---

### Post by su:bhatta on 2014-04-16
> **james120 said:**
>   I really can't decide if to partition my hard drive using easeus partition or windows disk utility or allowing the ubuntu install do it.  Which would you think would be better? 
Just make some unallocated space from your D drive i would say, if Windows is installed in C drive. 
Wherever Windows is, be it C or D, don't try to free space there, cause of the fragmentation problems inherent to Windows. 
I have used EaseUS and found it very competent for the task. Choose that it does not format the unallocated space to NTFS. 
 > Now I'm using the 64bit version of ubuntu to take advantage of the additional ram. Installed ram is 4gb.  I've got xp home 32bit version installed on a 1tb hdd.  Would it be ok to use the 64bit version?.
What is your CPU? if it is 64 bit architecture then go ahead with the AMD64 ISO. 
You dont need 64bit ISO to take advantage of the 4Gb RAM  as stated by **Impavidus**.
32Bit can use support upto 64Gb RAM.
 > Will I need to make the root a primary partition or or will the iso file do that for me?   Is the swap file installed on it's own partition?  Will the downloaded iso file do this?
Best to let Ubuntu partition manager handle this. When marking the partition you want to install root, you can select it to be a primary partition. 
Just remember you can make only 4 primary partitions in DOS.
> Also will the iso image fit on a cd or do I need to use a dvd.  I'll burn it using imageburn. The Ubuntu 64bit should fit on DVD & not CD.>    How much do I need for the swap file?  I'm not going to hibernate though, only use screen saver. It's a desktop computer.  How much for the root?  I know the rest will be used for the home folder. 

You don't have to select separate home and root partitions, and can use '/' as the mount point. 
300Gb is very fine . 
But if you choose separate root, then yes 20-30Gb should be sufficient, then again depends on how much additional stuff you install later. 

2Gb swap should be sufficient, if you want you can always make it bigger, but not required.

---

### Post by james120 on 2014-04-17
Sorry it took so long to get back.  Today I downloaded 14.04 and burned it to disk.  I'm almost ready to try it.  Could you answer for me some additional questions?  Do I need to create the partitions myself or will the installer do it?  Also if I have to do it would it be logical partitions or what?

---

### Post by james120 on 2014-04-17
I have 2 partitions on one drive.  600gb for windows and 300gb for the soon to be installed ubuntu.

---

### Post by james120 on 2014-04-17
The installer says install ubuntu alongside windows xp home edition or something else.  I selected something else.  It then gives me these selections:
/dev/sda i can highlight this, bit there's no check box for it
/dev/sda1  ntfs.  this is the windows installation
free space 355834 mb with checkmark box
/dev/sdb no check box
/dev/sdb1 ntfs 250056mb with check box i think this is my other internal hdd
I think i should check the free space.  am i right or should it be /dev/sda?
Sorry to be such a pest, but i'm trying not to get into trouble.

---

### Post by Impavidus on 2014-04-17
sda is your first drive, sdb the second drive, etc. sda1 is the first partition on the first drive, sda2 would be the second partition, sdb1 the first partition on the second drive, sda5 would be the first logical partition on the first drive. This includes both internal drives and external ones, like usb drives. I don't think the dvd is included in that, as you can't install Ubuntu there. sda1 and sdb1 are your Windows partitions, C and D (not necessarily in that order). You have 360GB unallocated space on sda. There you can install Ubuntu. You can create partitions there manually and set mountpoints. If you want to make things easy, you can select "install alongside Windows xp" and the installer will do everything automatically. It may not give you the perfect setup (no /home partition, swap may be larger than you want), but it will be quite OK.

Did we already tell you that you may need backups?

---

### Post by james120 on 2014-04-17
I used the free space and clicked add, then put 50gb for root, add 6gb for swap, and the rest for home.  I think it's ok.  It booted back up after restart and gave me a boot menu with ubuntu and windows.  I'll check my free space in a while.  Also does a desktop photo have to be a .png or can it be a jpg?  Permissions says "me" and read/write.  It also says james but i can't change the permissions to read/write on that one.  Hopefully it'll reload and the desktop photo will auto come back on without me having to install the photo again.  How can I place most used icons on desktop?  I'm  very happy that it worked for me as i was sweating for awhile.  Thanks

---


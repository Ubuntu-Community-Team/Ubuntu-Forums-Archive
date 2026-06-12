---
title: "Can't boot into Windows or Ubuntu after installing 14.04"
date: 2014-09-28
forum: New to Ubuntu
---

### Post by j3ff720 on 2014-09-28
Hi All! 

I am new here and don't know much about Ubuntu so I wanted to give it a try and dual boot it with windows 8.1.
I installed it and was able to get into GRUB and it wouldn't boot any OS that was listed. I then did some research and I ran boot repair.
After I ran boot repair and rebooted my laptop I get a black screen saying "Missing Operating System". Now the only way I can do something is through the Ubuntu CD. I can see my other partitions and files through the Ubuntu CD explorer so all my original files are there.

I got this from the boot repair: [http://paste.ubuntu.com/8451520/](http://paste.ubuntu.com/8451520/)

I would really appreciate your help. I need to get up and running as soon as possible for work and school tomorrow :/

---

### Post by yancek on 2014-09-28
You have syslinux installed to the master boot record of your hard drive.  Syslinux is usually used on Live CD/DVD or flash drives.  There are several Linux partitions but the boot repair output shows no Grub boot files.  Part of the problem is Dynamic disk indicated by the "SFS" partition type.  You can get a brief explanation of it at the link below:

[http://ubuntuforums.org/showthread.php?t=2102917](http://ubuntuforums.org/showthread.php?t=2102917)

---

### Post by j3ff720 on 2014-09-29
Thanks for the link. Would you recommend to install my laptop HDD in my desktop and format it from inside my desktop's OS? Or just installing everything from scratch?

---

### Post by yancek on 2014-09-29
From what I understand it won't matter if you are using SFS on the lapatop.  Never used it myself.  I doubt if installing it to your drive attached to the Desktop then attaching the drive to the laptop will make any difference but I don't really know as I've never used SFS>

---

### Post by Vladlenin5000 on 2014-09-29
Everything you need to know about the Microsoft proprietary dynamic volumes standard and its implications for a Ubuntu installation or dual-boot is in the thread you - yancek - already linked - [http://ubuntuforums.org/showthread.php?t=2102917](http://ubuntuforums.org/showthread.php?t=2102917) -, Post #2 (comments & links).

In a nutshell, you -[[COLOR=#000000] j3ff720[/COLOR]]("http://ubuntuforums.org/member.php?u=1947923")[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1947923") -  just made a mess. The best solution for your dual-boot is to clean that disk and start from scratch by installing Windows first in a standard NTFS partition leaving the required unallocated space for Ubuntu which will be installed later. Done.
The second best solution is to recover Windows by booting a Windows DVD (or USB), then use a third-party software to convert the dynamic partitions into basic partitions, then boot the live DVD (or USB) to reinstall Ubuntu.

---

### Post by j3ff720 on 2014-09-29
I was fearing that I would have to do that. thankfully I have all my files backed up. thanks for putting it bluntly. I don't know why the disk is dynamic in the first place.

---

### Post by j3ff720 on 2014-10-03
So I was able to work around the problem without losing all my data. 
Because my HDD was formatted as dynamic, I had an issue when trying to re-install windows. It said that I had an invalid disk.
After doing some research I  found a very helpful video that saved me [here]("https://www.youtube.com/watch?v=QQgRkEuFQac"). I installed my laptop HDD into my desktop and I followed the instructions in the video, rebooted and I was finally able to see the content of my HDD! :p
Afterwards I ran a backup of my OS partition. 
After that was done, I installed windows from scratch on the HDD and I restored the backup I did and its been working just fine.

I know this isn't an exact solution, but I hope it helps anyone in the future, just in case they find themselves in the same situation that I was in.
Hopefully my next run at Ubuntu will be much better.

---

### Post by Vladlenin5000 on 2014-10-03
I'm glad you did. Please mark this thread as solved, using the thread tools, so other can benefit.
For future reference, in intended dual-boot scenarios always check whether or not some proprietary format has been used in the already installed Windows and proceed accordingly. Running a live session and opening GParted to check the drives and partitions is always a good starting point. Now that you know what to look for you won't fall for the same trap.

---

### Post by oldfred on 2014-10-03
The solution you used only worked as the dynamic partitions still matched the physical partitions for most of your data. Since dynamic are logical partitions overlaying the physical partitions, they may get adjusted as you add even more partitions. If you have 4 dynamic or less and they match in size to the physical, the direct edit of the partition table will work, otherwise it could totally destroy partitions that do not match.

Testdisk would have also worked in that case also. But sizes must match including only 4 or less logical partitions. Several have posted they used testdisk but again that may not always work.

---


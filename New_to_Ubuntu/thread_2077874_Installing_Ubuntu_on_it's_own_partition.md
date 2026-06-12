---
title: "Installing Ubuntu on it's own partition"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by NoWayWin8 on 2012-10-29
Hi folks!

I've been test-driving Ubuntu for about 12 hours now. I did the "wubi" installation on a laptop and now I'm using Ubuntu on my desktop PC by running it directly off the DVD-ROM.

So far I love it! I'm ready to drop Windoze 7 down a well - but since I share both computers with family members who are, for the time being, not ready to abandon the familiar Microcrap setup, I think my best option is to install Ubuntu on it's own partition. This way I can get the full effect without disturbing the Win7 holdouts who use this computer.

What I want to do is give Ubuntu it's own partition while preserving all the files and settings already on the computer under Windows. 

Now, fair warning here - I'm smart, but I'm a total newbie at installing an OS by myself and have never partitioned a drive in my life. I don't want to accidentally erase something or corrupt the HDD. I guess my main questions are:

1. What is the best options as far as backing up my current installation prior to partitioning? Realistically, what sort of backup should I perform in order to safeguard the current installation? Should I backup using a disk image? Will that protect me against any sort of malfunction (short of frying the HDD) I could encounter if the partitioning doesn't go according to plan?

2. Can you recommend a link that explains exactly how to do the partitioning from start to finish - and most importantly allows the previous Windows installation to be used in exactly the same way as before by others who use this computer so their interface doesn't change?

Thanks so much for your time!

---

### Post by Androzani1 on 2012-10-29
> **NoWayWin8 said:**
> Hi folks!

I've been test-driving Ubuntu for about 12 hours now. I did the "wubi" installation on a laptop and now I'm using Ubuntu on my desktop PC by running it directly off the DVD-ROM.

So far I love it! I'm ready to drop Windoze 7 down a well - but since I share both computers with family members who are, for the time being, not ready to abandon the familiar Microcrap setup, I think my best option is to install Ubuntu on it's own partition. This way I can get the full effect without disturbing the Win7 holdouts who use this computer.

What I want to do is give Ubuntu it's own partition while preserving all the files and settings already on the computer under Windows. 

Now, fair warning here - I'm smart, but I'm a total newbie at installing an OS by myself and have never partitioned a drive in my life. I don't want to accidentally erase something or corrupt the HDD. I guess my main questions are:

1. What is the best options as far as backing up my current installation prior to partitioning? Realistically, what sort of backup should I perform in order to safeguard the current installation? Should I backup using a disk image? Will that protect me against any sort of malfunction (short of frying the HDD) I could encounter if the partitioning doesn't go according to plan?

2. Can you recommend a link that explains exactly how to do the partitioning from start to finish - and most importantly allows the previous Windows installation to be used in exactly the same way as before by others who use this computer so their interface doesn't change?

Thanks so much for your time!

OK, put a system image onto an external drive for starters.
Right click on Computer in the start menu and click manage.
Go to the disk management section.
Tell us if there is any unallocated space.

---

### Post by Mark Phelps on 2012-10-29
The main risk in setting up dual-boot is causing damage to Win7 by charging into it without taking the necessary precautions.  If you're serious about setting up dual-boot with Win7, then read ALL of the material below before you do anything else:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by NoWayWin8 on 2012-10-29
Unfortunately an external drive is something I lack... Is it useful to back it up on DVDs?

The computer currently has 411 GB of free space / 75 GB used.

---

### Post by deadflowr on 2012-10-29
This should give you more help:

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Along with what Mr Phelps has already said.

---

### Post by NoWayWin8 on 2012-10-29
Thank you deadflowr that link along with Mr. Phelps' advice is extraordinarily helpful. 8-)

---

### Post by RLDr on 2012-10-29
First backup your data to external medium.

THEN

Follow every step (screen shoot etc.) carefully of the following pages:

1.
[Dual Boot Windows 7 and Ubuntu 12.04 (Precise Pangolin)]("http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/")

2.
[How to install Windows 7 and Ubuntu side by side]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")

---

### Post by Bashing-om on 2012-10-29
NoWayWin8; Hi ! Belated WELCOME to the forum.

There exist lots and lots of help (and various tutorials) -> welcome in general to ubuntu !

Feel free to ask questions and gain our comments for any event/consideration. This is a broad spectrum forum.

We are here to aid and assist.

[INDENT][INDENT]warm regards <==BDQ
 
[/INDENT][/INDENT]

---

### Post by NoWayWin8 on 2012-11-04
Thanks so much! I'm actually in the middle of the process as we speak. I made a DVD system image backup (took up 4 DVDs for the whole thing) and I just now used Windows disk management to shrink the windows volume.

Current size:
  0.39GB - OEM Partition
 12.25GB - Recovery
241.38GB - OS (C;)
212.09GB - Unallocated

So far so good. Restart with the Ubuntu boot disk, select "Install Ubunutu", then "Install alongside Windows" and the installation program does the rest. :)

Easy! That was a great suggestion to use the shrinking tool in Windows Disk Management - makes it so I don't have to deal with that ominous "unbootable windows" error that comes from using GParted.

Windows --> Plonk! Flush!

---

### Post by NoWayWin8 on 2012-12-13
Just to give an update, I've been using Ubuntu exclusively on the desktop PC ever since the last post. Other than logging into WIndows a couple of times to retrieve passwords stored in Firefox, I haven't looked back.

Thanks for you help, guys (or girls as the case may be). 8-)

---

### Post by Mark Phelps on 2012-12-13
Good to see it worked out OK for you.

Please use the Thread Tools and mark this thread as SOLVED.

---


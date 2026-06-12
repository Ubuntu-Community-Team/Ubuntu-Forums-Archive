---
title: "I can't install ubuntu!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by dsifaka on 2008-08-06
My problem comes at the end when it is making the partitions. I'm using a guided set up because i have very, very little knowledge of ubuntu or any other linux based operating systems. It always says when it goes to format the partion "failed to create a file system" and in that it says "the ext3 file system creation in partition #1 of SCSl1 (0,0,0) (sda) failed. 
Please help! 
It lets me use it as a live session user but i would like to keep it on the hard drive.

---

### Post by Het Irv on 2008-08-06
Have you had problems with the hard drive before?  When you were running a different operating system, perhaps?

---

### Post by yragrelluf on 2008-08-06
are you using the right distribution for your computer?
are you setting up a dual boot or trying to use ubuntu only?
are you sure you checked guided, use entire disk?

---

### Post by dsifaka on 2008-08-06
Not that I know. I just got the computer, but it is fairly old. Could i set up the partitions manually? If so how can i set them up?

---

### Post by dsifaka on 2008-08-06
my computer has all the necessary specifications, i am trying to use only ubuntu, and i checked for it to use the entire drive

---

### Post by yragrelluf on 2008-08-06
select manual, and delete any existing partitions. when the entire hard drive shows up as free space then you need to make an ext3 partition for / this will hold your operating system, and should be at the beginning. The next step will be to create a partition for swap, that should be at the end. Then finally, partition the rest of the free space as ext2 to use as /home
it is up to you how big each partition will be. my computer is 160gb, and i use 5gb for swap, 55gb for /home, and 100gb for /
the partition editor on the live cd has a decent gui, so take your time and think about everything you are doing, if you do it right, you should be able to install and reinstall any OS on the / partition, without creating a new swap, or losing your files.
let me know how it goes!

---

### Post by Het Irv on 2008-08-06
The partitioning may have failed because of a hard drive failure, if the manual partitioning fails, you may have a hardware problem.

---

### Post by yragrelluf on 2008-08-06
> **Het Irv said:**
> The partitioning may have failed because of a hard drive failure, if the manual partitioning fails, you may have a hardware problem.

good point. was the computer working at all when you got it?

---

### Post by dsifaka on 2008-08-06
the computer had no OS but entered BIOS

---

### Post by dsifaka on 2008-08-06
you were right. the help with setting up the partitions helped a lot and i was able to move pass that problem but when it started to copy the files it said that the hard drive was probably faulty. Thank you for your help, i may just try to get a new hard drive now.

---

### Post by yragrelluf on 2008-08-06
sorry to hear it. but if you are bored you could boot it up to the bios and there may or may not be a disk utility that may be able to fix the problem. also, you could download a gparted livecd and see if that can get you going. most hard drive problems can be fixed unless a magnet or something came near it, but its up to you how hard you want to try, maybe installing windows, and defragmenting several times, then installing ubuntu. good luck

---


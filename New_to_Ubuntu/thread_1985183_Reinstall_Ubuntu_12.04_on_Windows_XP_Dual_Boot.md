---
title: "Reinstall Ubuntu 12.04 on Windows XP Dual Boot"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by achschade on 2012-05-23
I use a PC at work that's partitioned with Windows XP and Ubuntu. Last week I did the daily upgrades and ended up getting a blank screen upon restarting, and after a lot of help from a colleague ended up reinstalling Ubuntu from a flash drive. So now I have version 12.04 (I had 11.10 before I think). 

My problem is that when we reinstalled, we did it so that all my files were saved, but I think it did it in a sort of weird way. When I go to my home folder now, there is a "37 GB Filesystem" that appears to be my old Ubuntu files. I had to mount it to get to my old files, which I have already moved over, but I can't get rid of the file system. The thing is, I only have 9 GB of usable space... it sort of seems like it created another partition with my old filesystem and made it huge, and the little bit that I have left is what I can use. Not really sure if that makes sense though. The hard drive is 80GB, and the windows side is only 30GB, so I know there is more than 9GB of space on there. 

Unless there is a way to fix this without reinstalling, I was thinking of just doing a clean reinstall, without saving my files (I have things backed up elsewhere already anyway) and starting fresh. Unfortunately, I don't know how to do this while keeping the Windows XP partition intact (I didn't create this partition, it was already done for me, so I have no idea how this works). If anyone has any advice on doing the reinstall, or on fixing this space issue without reinstalling, I would be very appreciative.

---

### Post by Miljet on 2012-05-23
Please open a terminal (Cont + Alt + t) and type in the following
```
sudo fdisk -l
```
It will ask for your password. It will not appear to be accepting the password, but it is. Just type in the password and hit enter.

Then copy the output of that command and paste it here in another post. That way we can see just how your disk is partitioned and can advise how to proceed.

Thank you.

---

### Post by achschade on 2012-05-23
Okay, I did that. Here is the output:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1c9e1c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63488879    31744408+   7  HPFS/NTFS/exFAT
/dev/sda2        63488880    67681844     2096482+  82  Linux swap / Solaris
/dev/sda3        67681845    84068144     8193150   83  Linux
/dev/sda4        84068145   156248189    36090022+  83  Linux

---

### Post by audiomick on 2012-05-23
Servus!

It looks to me like your new install is on sda3, and your old files on sda4.

Have a look yourself with the Hard Drive utility. It should be clear, I think, if nothing else then from the size of the partitions.

sda1 is the windows install, of course, and sda2 is your swap.

You have two options: the first is, once you are really sure that you have everything safely backed up, and that sda4 is really the partition from the old install and sda3 that from the new install, simply erase sda4 and expand sda3 into the then empty space. You should do this from the live environment, i.e. booted into the "try ubuntu without installing" option from the install CD or USB drive. 

The second option is a little more complicated, and involves  a fresh install. I personally would consider this for two reasons: I like to have a seperate /home partition, and I don't like having all four of the possible primary partitions used and no room to add new ones should the need arise.

On modern machines, the limitation of only four primary partitions is no longer current, I believe, but I can't remember the details, and since the machine has XP on it, I asssume it is old enough for the rule to still apply.

Anyway...

I would consider, having backed up everything off the old Ubuntu install, removing sda2, sda3 and sda4 and replacing them with and extended partition. Inside of that, I would do  fresh install with swap a little bigger than the amount of RAM the machine has, a partition for the system, mounted at / and around 12 GB, and the rest mounted at /home as a separate /home partition.

The advantage of a separate /home is that if you have to re-install, you can simply re-mount it to the new install.

If you don't need the hibernate function to work, you can get away with less swap. You can get a feel for this by watching the system monitor a bit whilst you work to see how close you get to using the swap with your normal workload. I know of a least one bloke who doesn't have any swap at all, but I reckon that is pushing the point a  bit.

The advantage of having everything in an extended partition is that you can add another partition or two simply by shrinking down the ones you have and putting a new one in the empty space.  I have to admit, though, that this sounds unlikely on that machine, as the drive isn't all that big to start with.

---

### Post by wilee-nilee on 2012-05-23
I would just add that 4 primaries on a mbr set up on a single drive is still the limit. Or 3 primaries and a extended.

---

### Post by achschade on 2012-05-24
Ok. Just erasing sda4 and then expanding sda3 sounds a little simpler. So let's say I boot from a usb and click on "try ubuntu without installing". Now what exactly do I do to delete/resize partitions? Can I do it in Disk Utility? Or is there a better way?

---

### Post by achschade on 2012-05-24
I booted from a USB and used GParted to delete the empty sda4 and expand sda3 and it was a lot easier than I thought it'd be... Thanks for the help.

---

### Post by jtarin on 2012-05-24
Mark the thread solved.

---

### Post by audiomick on 2012-05-25
> **achschade said:**
> I booted from a USB and used GParted to delete the empty sda4 and expand sda3 and it was a lot easier than I thought it'd be... Thanks for the help.

Well done. :popcorn:

---

### Post by Miljet on 2012-05-25
Good deal! Glad you got it worked out.

---


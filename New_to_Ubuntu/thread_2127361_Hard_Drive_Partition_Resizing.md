---
title: "Hard Drive Partition Resizing"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by PoeticTorment on 2013-03-19
I used the Windows 7 installer for Ubuntu 12.04lts dual boot and after using it, I would like more hard disk space for Ubuntu. 
How can I make the Ubuntu partition bigger without erasing anything on either partition? About 70% of Windows partition happens to be un-used. I am a new Ubuntu user, so if you could simplify that would be a great help.

---

### Post by Impavidus on 2013-03-19
Do I understand correctly this is a wubi install? In that case [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

The limit is 30GB. If you want more you'll have to move to a true dual boot: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by PoeticTorment on 2013-03-20
I believe so, since it was downloaded on windows. 
I did try to resize Wubi but it did not want to work, I kept getting "Possibly non-existent device?" or "command not found."

Seem's I'm missing something, any thoughts that could help?

---

### Post by fantab on 2013-03-20
> **Impavidus said:**
> Do I understand correctly this is a wubi install? In that case [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

The limit is 30GB. If you want more you'll have to move to a true dual boot: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

+1.

Unistall Ubuntu from Windows, if you want more disk space than 30GB. Install ubuntu on its own partiton and dual boot.

---

### Post by Impavidus on 2013-03-20
> **PoeticTorment said:**
> I believe so, since it was downloaded on windows.

Most of us download on windows, but the point is whether you burnt the download to a dvd or flash drive, booted from that and installed, or that you ran the installer inside windows. If you issue the command```
sudo fdisk -l
```in a terminal it will become clear.
(You'll have to enter your password and hit enter. It won't show up in the terminal, but it will be accepted.)

And if you want to do a clean install as dual boot as fantab suggested, remember to make backups of every file you created in Ubuntu, as the original data will be lost. And also make backups of your windows, because you never know.

---

### Post by Mark Phelps on 2013-03-20
Setting up a true dual-boot with Win7 and Ubuntu is more involved than just booting from a disk and resizing the partitions.

If you want to use a true dual-boot, instead of Wubi, be sure to read through the details below before attempting it:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by PoeticTorment on 2013-03-22
Thanks for the tips, I got the partition taken care of.

---

### Post by fantab on 2013-03-23
If you tell the forum how you "got the partition taken care of", then it will help others who may have a similar issue.

---

### Post by PoeticTorment on 2013-03-29
I uninstalled Wubi, partitioned my windows, and then re-installed Ubuntu.
Sorry for not posting it earlier, didn't have much time to post anything. 
Thanks so much for the help!

---


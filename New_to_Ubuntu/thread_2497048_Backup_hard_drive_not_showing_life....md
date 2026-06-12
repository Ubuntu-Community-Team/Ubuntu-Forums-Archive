---
title: "Backup hard drive not showing life..."
date: 2024-04-21
forum: New to Ubuntu
---

### Post by Innernet on 2024-04-21
Hi.
My external USB hard drive used **only** for data backup once a year is not reporting contents.  It may have suffered a power outage the last time plug-in / turn-on.   There is no operative system in it.

How to fix errors, scan, repair, restore files ?

---

### Post by Innernet on 2024-04-21
It shows as USB being connected;  clicking mount does nothing.   Does show in 'files' as 'error mounting'

---

### Post by yancek on 2024-04-21
It is usually a good idea to do a backup more than once a year.

If there was a power outage while the disk was plugged in, you should run a filesystem check on the various partition filesystems.  Which filesystem is it?  Did you run parted or fdisk to get the device/partition name so you can run fsck (if Linux)?  Does the drive show with either of the above commands?  Have you tried mounting it after creating a specific mount point in a terminal?

---

### Post by Innernet on 2024-04-21
Thanks.  
I do not think there is partitions; the whole drive has for 15 years been as single data archive dump place with never an operative system in it.
Has a handwritten by me sticker "NTFS" on the drive case.  No fdisk nor fsck ever that I can remember.  I do not know what is a 'mount point' nor how to make it or if it is necessary.  Have never been used with Windows.

---

### Post by ajgreeny on 2024-04-21
If it really has an ntfs filesystem on it you will need to attach it to a Windows OS and run chkdisk on it, something that is impossible to do using Linux utilities.

If you no longer have Windows it would make much more sense to reformat the disk/partition to a Linux filesystem such as ext4.
You should also check again the disk partition layout with command 
**sudo fdisk -l**
That's a lower case L at the end, not figure 1.
Formatting a disk without a partition is not a sensible idea and I don't think its even possible to do in Linux.

---


---
title: "Seagate FreeAgent Destop External HDD is only accessible in Ubuntu and not in Windows"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by QMarshall on 2012-07-09
I'm a beginner and have only been using Ubuntu Linux for a year now. My Seagate FreeAgent Desktop 500GB External HDD was accessible in both Ubuntu Linux and Windows before but after the upgraded to Ubuntu 11.04 it's only accessible in Ubuntu and not Windows and I don't know How to fix this because I also need to use it with Windows.

---

### Post by MichaelGld on 2012-07-09
> **QMarshall said:**
> I'm a beginner and have only been using Ubuntu Linux for a year now. My Seagate FreeAgent Desktop 500GB External HDD was accessible in both Ubuntu Linux and Windows before but after the upgraded to Ubuntu 11.04 it's only accessible in Ubuntu and not Windows and I don't know How to fix this because I also need to use it with Windows.


Check the filesystem on the device. Windows cannot see any of the native Linux filesystems, such as ext3 or ext4.  If that's the case, copy all your files to other media then reformat the drive to ntfs.

---

### Post by QMarshall on 2012-07-09
How do I check the filesystems?

---

### Post by MichaelGld on 2012-07-09
> **QMarshall said:**
> How do I check the filesystems?

One way is to run Disk Utility.  On the left side under Storage Devices, click on the drive in question.  Then on the right part of the screen about halfway down is a graphical representation of your partitions.  In there it will tell you what filesystem is in use.

---

### Post by QMarshall on 2012-07-10
While checking what filesystem is in use I got this feedback:
 
Error checking filesystem on volume

An error occured while performing an operation on "Vincent External" (Partition 1 of Seagate FreeAgentDesktop): The device is busy

Details
Device is mounted and no online capability in fsck tool for file system

What does all this mean and how do I do now?

---

### Post by MichaelGld on 2012-07-10
> **QMarshall said:**
> While checking what filesystem is in use I got this feedback:
 
Error checking filesystem on volume

An error occured while performing an operation on "Vincent External" (Partition 1 of Seagate FreeAgentDesktop): The device is busy

Details
Device is mounted and no online capability in fsck tool for file system

What does all this mean and how do I do now?

Sounds like your partition may be corrupt.  Are you able to access it while in Windows?

---

### Post by sudo smith on 2012-07-11
Try unmounting it by right clicking its icon on the side dock and clicking unmount or something like eject or remove hardware safely. Then see what file system it is again. If that fails run gparted (search it in dash) and it should tell you what filesystem it is.

---

### Post by Grenage on 2012-07-11
> **QMarshall said:**
> I'm a beginner and have only been using Ubuntu Linux for a year now. My Seagate FreeAgent Desktop 500GB External HDD was accessible in both Ubuntu Linux and Windows before but after the upgraded to Ubuntu 11.04 it's only accessible in Ubuntu and not Windows and I don't know How to fix this because I also need to use it with Windows.

If it *was* working in Windows, then you know it is probably a FAT32 or NTFS.  The easiest thing to do is simply reformat it, so you'll need to copy the data elsewhere; you can repartition and reformat the drive in Windows, or in Linux.

If you use Linux, I recommend gparted:

```
gksu gparted
```
If it's not installed, install it using:
```
sudo apt-get install gparted
```
(or install it using the Software Centre).

---

### Post by QMarshall on 2012-07-11
The drive appears in Windows but it's not accessible at all.

---

### Post by Grenage on 2012-07-12
The drive is assigned a letter, and you can see the files - or windows just acknowledges that it's been plugged in?

---

### Post by QMarshall on 2012-07-12
The drive is assigned a letter but you cannot see the files.

---

### Post by Grenage on 2012-07-12
In which case, I would probably copy the data off while using Ubuntu, then repartition and format the drive.

---

### Post by David Andersson on 2012-07-12
> **Grenage said:**
> In which case, I would probably copy the data off while using Ubuntu, then repartition and format the drive.

I think we should determine what is wrong before we decide to reformat. The current project is to find out what kind of file system is on it.

[QUOTE=QMarshall]
While checking what filesystem is in use I got this feedback:

Error checking filesystem on volume
[/QUOTE]

Did you click "Check filesystem" in Disk Utility? No need to do that. (It is not the same as "Check WHAT filesystem"). When you have selected a Storage Device on the left, just look on the map of the drive (Volumes), and see if the file system is "ext4" or "ntfs" or something else. If unclear, click on the partition in the map and look at the "Type:" field, if it is "ext4" or "ntfs" or something else.

---

### Post by Grenage on 2012-07-12
> **David Andersson said:**
> I think we should determine what is wrong before we decide to reformat. The current project is to find out what kind of file system is on it.

Given that it did work (and was therefore either FAT or NTFS, and Windows-accessible), doesn't that make it a moot point?

---

### Post by QMarshall on 2012-07-12
This is the feedback I get when I select the Storage Device on the left

Usage:           Filesystem
Partition Type:  HPFS/NTFS(0x07)
Partition Flags: -
Type:            NTFS
Label:           Vincent External

---

### Post by David Andersson on 2012-07-13
> **QMarshall said:**
> This is the feedback I get when I select the Storage Device on the left

Usage:           Filesystem
Partition Type:  HPFS/NTFS(0x07)
Partition Flags: -
Type:            NTFS
Label:           Vincent External

Just to be sure we look at the right partition. Does the "Capacity:" field show the capacity you would expect? (About the right amount of gigabytes?)

Is the partition mounted? (Look at field "Mount point:")

If not, click "Mount Volume" and see if it can be mounted. Maybe you want to look around, but don't change any files there (if linux is doing something funny with ntfs). Then un-mount it.

Is the disk healthy? (Look at field "SMART Status:")

Will Windows see that there is a disk, but refuse to mount it, or does it not even see the disk? If it sees the disk, try a file system check from within Windows.

---


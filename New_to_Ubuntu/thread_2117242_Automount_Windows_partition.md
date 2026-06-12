---
title: "Automount Windows partition"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Garrigus Carraig on 2013-02-17
I'm transitioning from Windows to Ubuntu and still have all my files on my Windows Vista partition. I am trying to mount the Windows Vista partition at startup. After some research, I performed the following two steps:

[LIST=1]
[*]```
sudo mkdir /media/ACER
```
[*]Added this line to /etc/fstab : ```
UUID=FAA44061A440228D /media/ACER ntfs user,locale=en_US.utf8 0 0
```
[/LIST]
On reboot, the partition indeed mounts, but Nautilus also displays a ghostly twin in the sidebar, also called "ACER". (See attached picture.) Clicking on it yields an error message:
> Unable to mount ACER
Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command.
Ideally I'd like for that twin not to appear. However, I read in another thread that mounting that partition read-write could cause Windows to become annoyed. So my question is two-fold:

[LIST=1]
[*]Is it advisable that I work like this, running Ubuntu and working on the files on the Windows partition?
[*]If so, how do I have the Windows partition automount at startup without that ghostly twin?
[/LIST]
I close with some relevant information that might be helpful.


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=da0386dc-ba3b-4431-9d8a-ce53ffba814b /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4d19dbc8-a483-4dba-bed9-ee7de12cb2af none            swap    sw              0       0
# Automatically mount ACER Windows drive
UUID=FAA44061A440228D /media/ACER ntfs user,locale=en_US.utf8 0 0
```
```
sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52c031f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  27  Hidden NTFS WinRE
/dev/sda2   *    20467712   205862911    92697600    6  FAT16
/dev/sda3       205862912   298399735    46268412    7  HPFS/NTFS/exFAT
/dev/sda4       298399744   390721535    46160896    5  Extended
/dev/sda5       298401792   376225791    38912000   83  Linux
/dev/sda6       376227840   390721535     7246848   82  Linux swap / Solaris
```
```
sudo blkid


/dev/sda1: LABEL="PQSERVICE" UUID="7E5829D9E49BED2A" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="FAA44061A440228D" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="2E9AB0219AAFE395" TYPE="ntfs" 
/dev/sda5: LABEL="UbuntuOS" UUID="da0386dc-ba3b-4431-9d8a-ce53ffba814b" TYPE="ext3" 
/dev/sda6: UUID="4d19dbc8-a483-4dba-bed9-ee7de12cb2af" TYPE="swap" 

```

---

### Post by WhipLash365 on 2013-02-18
1. Well, I used to work like that for a long time, and never had any problems with it.
2. Try to do it using Disk Utility (Right click on partition -> mounting options, disable auto managing and set it to mount on startup [if i remember right])

---

### Post by Impavidus on 2013-02-18
Nautilus lists partitions mounted in /media, because that's where any auto mounted drives (dvd, usb) go as well. If you mount the windows partition somewhere else (like /mnt, but it doesn't really matter at all), it should go away.

Windows may not like it when you write to the partition where windows is installed, so it's often better to mount that partition read-only. Mounting your DATA partition read-write should be no problem.

---

### Post by Mark Phelps on 2013-02-18
You're not hibernating Windows while you are in Ubuntu, are you? Because if you are, any changes made to Windows while in Ubuntu run the risk of corrupting that partition.  If you're going to access Windows while running Ubuntu, you need to disable hibernation in Windows.

---

### Post by Garrigus Carraig on 2013-02-18
> **Impavidus said:**
> Nautilus lists partitions mounted in /media,  because that's where any auto mounted drives (dvd, usb) go as well. If  you mount the windows partition somewhere else (like /mnt, but it  doesn't really matter at all), it should go away.

Windows may not like it when you write to the partition where windows is  installed, so it's often better to mount that partition read-only.  Mounting your DATA partition read-write should be no problem.

I took this to heart & moved my data to the DATA partition. Automounting to /mnt seems to be working fine.

> **Mark Phelps said:**
> You're not hibernating Windows while you are in Ubuntu, are you? Because  if you are, any changes made to Windows while in Ubuntu run the risk of  corrupting that partition.  If you're going to access Windows while  running Ubuntu, you need to disable hibernation in Windows.
I don't think so. I've never seen the hibernation option in Windows. Most days I never boot into Windows; I just mount that drive. But regardless, this is good to know.

Thanks to all of you for your help.

---


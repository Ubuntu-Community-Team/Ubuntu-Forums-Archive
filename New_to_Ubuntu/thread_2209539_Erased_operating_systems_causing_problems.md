---
title: "Erased operating systems causing problems?"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by bjngchn on 2014-03-06
I'm trying to install kubuntu/lubuntu on whole disk with encryption. when I was even more naive, I never had problem installing. Now everytime there is a a problem, and a different problem for each version and each computer. I don't think this is a coincidence. One of the problems is related to partitions. Creating partition/volume failed; or there is a partition causing problems. All these don't make any sense. If I'm trying to erase everything, why is this not done automatically, and I get errors instead. I was thinking I erased windows years ago, but maybe windows is still there and eating lots of memory, even if it doesn't run, because there is a partition belonging to windows or previous OS, and new installation prefers not to touch it for unknown reason. This is the impression I get, maybe correct maybe false, but either way something doesn't make any sense in any case.  .... If old partitions are likely to cause problems, I prefer to delete them completely if possible.

---

### Post by Mark Phelps on 2014-03-06
> but maybe windows is still there and eating lots of memory, even if it doesn't runAn OS does NOT consume any memory when it is not running.

What you may be encountering, on older drives, is that the MBR (Master Boot Record) exists outside any of the partitions, so even if you remove the OS that was in place when you last modified the MBR, the MBR remains behind.  So, an MBR that was modified to boot Windows (which is done automatically when Windows is installed) will still try to boot Windows even if all the Windows partitions are erased.  Same is true of an MBR that was modified to boot Linux.

---

### Post by grahammechanical on 2014-03-06
I have noticed that sometimes when an installation fails for the reason you have it seems as if the installer remembers the problem and continues to stumble at the same point.

You may find that you do indeed need to delete that partition or at, least format it using the Disks utility instead of the installer (Ubiquity). What file system are you using and what version of Ubuntu?

A few months ago I tried to install Trusty Tahr on btrfs and it failed at the creating the partition/file system stage and from then on the installer would fail at that pint whether the chosen files system was btrfs or Ext4. I then had to format the partition as Ext4 using Disks so that the installer would install Ubuntu on it as an Ext4 file system. 

Regards.

---

### Post by bjngchn on 2014-03-14
Good answers.. I don't even know what a filesystem is. I try some version of *ubuntu to erase whole disk, until it works. .. New questions based on your asnwers: Any magic command which shows all partitions, and anythng else, like MBR, filesystems? Can't we erase MBRs? ... Can we experiment with partition manager, or LVM (no idea what they are/do) safely, or a big failiure is likely if we don't know what we are doing.  Can we, as naive users,  make sure some directories are written to one partition, others to another.  (I understand questions may be diverging..)...... Here is one way, I suspect , may help us know whether there are hidden partitions. Bios tells us how much total space we have, and we can compare it with  partitions in current installation.

---

### Post by Mark Phelps on 2014-03-15
There are several commands that show the partitions on a drive, fdisk and gdisk (for GPT formatted drives) come to mind.  They don't show the contents of the MBR.

An easy way to see if there are any hidden partitions is to use one of the popular partition tools: Gparted or Disks.  Both are GUI based and both will show ALL the partitions present on a drive, hidden or otherwise.

You can "experiment" with partition tools all you like, but if you do something disastrous, you risk trashing the data on the drive.

As to writing directories to specific drives, if you're talking about doing to have different pieces of an app installed to different drives, the answer basically is NO.  There are specific folders in the Linux filesystem that are used for specific purposes, and when an app is installed, the different components are written to the proper directories.  If you mess around with this, you risk trashing your system.

---


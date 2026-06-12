---
title: "Why gparted auto-mounts in liveCD?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-18
While using GParted (in Ubuntu 8.04 liveCD) to copy a partition from one drive to another.  Let's say I want to copy /dev/sdb1 to unallocated space on /dev/sda), I noticed the following:

[LIST=1]
[*]Select /dev/sdb1 and "copy partition"
[*]Select unallocated space on /dev/sda and choose "paste"
[*]Select "apply"
[*]I get an error that says that I can't copy because /dev/sdb1 is mounted
[*]I look at the partions on /dev/sdb
[*]All the partitions on /dev/sdb are mounted
[*]I unmount partition /dev/sdb1, and things look okay
[*]AGAIN:Select /dev/sdb1 and "copy partition"
[*]AGAIN:Select unallocated space on /dev/sda and choose "paste"
[*]AGAIN:Select "apply"
[*]AGAIN:I get an error that says that I can't copy because /dev/sdb1 is mounted
[*]Look at /dev/sdb and all partitions are mounted again
[*]Then I try an experiment:
[INDENT][LIST=1]
[*]Unmount /dev/sdb1... okay
[*]Unmount /dev/sdb2... okay but /dev/sdb1 auto-mounts
[/LIST][/INDENT]
[/LIST]

It seems that one drive(device) has to have (it seems) all-but-one of it's partitions mounted at a time.  And the other drive(device) doesn't have to have any partitions mounted.  My work-around was to go to my desktop and unmount (using right-click "unmount") all partitions on /dev/sdb and then make sure some partitions on /dev/sda were mounted.

So now the question:

[SIZE="3"]How do I control which drive has to have some/all partitions mounted when I'm using GParted in Ubuntu 8.04 liveCD?[/SIZE]

---

### Post by Titan8990 on 2008-11-18
Personally, I would either use dd or it's GUI equivalent, PartImage for what you are trying to do.

To copy sdb1 to sda = 

sudo dd if=/dev/sdb1 of=/dev/sda


ALL data on /dev/sda will be lost. Use dd with caution.

---

### Post by boof1988 on 2008-11-18
> **Titan8990 said:**
> Personally, I would either use dd or it's GUI equivalent, PartImage for what you are trying to do.

To copy sdb1 to sda = 

sudo dd if=/dev/sdb1 of=/dev/sda


ALL data on /dev/sda will be lost. Use dd with caution.

Thanks for the response.

I have PartImage... but it's options are still a bit of a mystery to me.  That's why I'm using GParted (for now).  Hope to understand how PartImage and "dd" work in the future, but they're just a little too mysterious for now.  I figure if GParted is doing something weird, it may be for my own good.  And I'd just like to know why.

---

### Post by egalvan on 2008-11-18
From what I know of GRUB, it mounts by hard drive,
sda
sdb
sdc

the partition table resides on a hard drive, and controls all the partitions on that hard drive.
When you access a  partition, the partition table is "locked", and you can't alter any other partition controlled by that table.

Further, my experience is that GRUB does not 'auto-mount' drives or partitions..
 I need to explicitly mount any drive or partition.

Anyone have anything to add?
Linux Gurus, where are you?

---

### Post by boof1988 on 2008-11-18
Thanks, egalvan, for the reply.

> **egalvan said:**
> From what I know of GRUB, it mounts by hard drive,
sda
sdb
sdc

the partition table resides on a hard drive, and controls all the partitions on that hard drive.
When you access a  partition, the partition table is "locked", and you can't alter any other partition controlled by that table.

Thanks for the info.

> **egalvan said:**
> Further, my experience is that GRUB does not 'auto-mount' drives or partitions..
 I need to explicitly mount any drive or partition.

I'm using the Ubuntu liveCD so I don't think the GRUB is *still doing stuff* once the OS is going. *dunno*  I'm still trying to learn how to see the MBR so I can understand what is occurring during boot.  I can see the GRUB's menu.lst but I don't know how it relates to MBR.

---


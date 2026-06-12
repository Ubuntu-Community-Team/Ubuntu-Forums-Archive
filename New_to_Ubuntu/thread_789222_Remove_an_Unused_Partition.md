---
title: "Remove an Unused Partition"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by wagb278 on 2008-05-10
Using Ubuntu 8.04 (64-bit). Two SATA hard disks, one has two  partitions but one of the partitions is not used in this configuration - but does appear in the list (Places-->Filesystem).

Looking at the Permissions for this partition - all datums report "unknown" with Location reporting "computer:///"

How, if possible, do I prevent this partition from showing up.  This partition was created in case I want to dual boot another version of Ubuntu, or Linux distribution, and is currently empty. It is not in fstab, and is not mounted.  I would prefer that this partition not be know to this Operation System.

This partition is sdb1 (second disk, first partition) if that makes a difference.

Inspecting the disks with Gparted, I notice that there are "Flags" available (none checked) and one of these is "hidden".  If I check this flag does it Hide the partition just for the current OS - or will that partition disappear forever?

Thanks

---

### Post by kirios on 2008-05-10
To be **really** sure you don't need the partition: 
Applications > Accessories > Terminal, run **mount** and **sudo fdisk -l**. If it's unused (unformatted, according to your post), run **sudo parted hard_disk_name** (e.g., /dev/hda or /dev/sdb), type **p** to review your partitions, then **rm partition_number**, and **q** to exit.

> **wagb278 said:**
> Using Ubuntu 8.04 (64-bit). Two SATA hard disks, one has two  partitions but one of the partitions is not used in this configuration - but does appear in the list (Places-->Filesystem).

Looking at the Permissions for this partition - all datums report "unknown" with Location reporting "computer:///"

How, if possible, do I prevent this partition from showing up.  This partition was created in case I want to dual boot another version of Ubuntu, or Linux distribution, and is currently empty. It is not in fstab, and is not mounted.  I would prefer that this partition not be know to this Operation System.

This partition is sdb1 (second disk, first partition) if that makes a difference.

Inspecting the disks with Gparted, I notice that there are "Flags" available (none checked) and one of these is "hidden".  If I check this flag does it Hide the partition just for the current OS - or will that partition disappear forever?

Thanks

---

### Post by wagb278 on 2008-05-11
> **kirios said:**
> To be **really** sure you don't need the partition: 
Applications > Accessories > Terminal, run **mount** and **sudo fdisk -l**. If it's unused (unformatted, according to your post), run **sudo parted hard_disk_name** (e.g., /dev/hda or /dev/sdb), type **p** to review your partitions, then **rm partition_number**, and **q** to exit.

Thanks for the reply.

If I do what you suggest will that remove the partition from the disk?  I want to retain that chunk of disk space for use latter. Maybe I should not have set that at the beginning of the disk, but I wanted it not to be a logical partition - so it is at the beginning of the disk.

For people who set up a dual boot (say with Windoze) see the partition for the other OS while running Ubuntu?  

I don't want to see this other partition - which will contain another OS, someday.

---

### Post by snooptodd on 2008-05-11
hiding the partion with gpared will not remove the partion it is still there, it might work for you give it a try. You can always go back into gparted and set it back.

---

### Post by kirios on 2008-05-11
> **wagb278 said:**
> If I do what you suggest will that remove the partition from the disk?  I want to retain that chunk of disk space for use latter. 

**Yes, it will delete the partition. You will have free space at the beginning of the disk. If you intend to install another OS, just use its installer to create a new primary partition in the unallocated space.** 

> **wagb278 said:**
> Maybe I should not have set that at the beginning of the disk, but I wanted it not to be a logical partition - so it is at the beginning of the disk.

For people who set up a dual boot (say with Windoze) see the partition for the other OS while running Ubuntu?  

I don't want to see this other partition - which will contain another OS, someday.

**I'm not sure I understand why it matters whether you see an unused partition in Places > Filesystem. Anyway, Ubuntu does see Windows and other partitions in a dual-boot system. In fact, it defaults to making an entry for each partition in /etc/fstab so that you can access the other filesystems.** 
  
> **wagb278 said:**
> Inspecting the disks with Gparted, I notice that there are "Flags" available (none checked) and one of these is "hidden".  If I check this flag does it Hide the partition just for the current OS - or will that partition disappear forever?

**AFAIK you'll have to unhide it to install the other OS, so it will show up in Places > Filesystem anyway. :-)**

*EDIT: It would make it easier if you could run **sudo fdisk -l** in terminal and post the output here.*

---

### Post by wagb278 on 2008-05-12
Thank you - all

I guess I will just leave it alone and let it show up.  I know what it is really not a big deal.

---


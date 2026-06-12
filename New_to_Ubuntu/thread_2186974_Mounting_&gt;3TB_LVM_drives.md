---
title: "Mounting &gt;3TB LVM drives"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by matej.cucek on 2013-11-10
Hello

I am having a bit of an issue.
I am on a 64bit ubuntu 12.04 desktop setup.
I was able to create a sequential group LVM with a 3TB drive and a 1.5TB drive.
The LVM tool in ubuntu shows that the group volume is 4191.78GB in size and the available space is fully extended
The disk tool shows 4.5TB size for the group volume.

```
cat /proc/partitions
```
 output:
```
major minor  #blocks  name

   8        0  488386584 sda
   8        1   15624192 sda1
   8        2  244141056 sda2
   8       16 2930266584 sdb
   8       17 2930265088 sdb1
   8       32 1465138584 sdc
   8       33 1465137152 sdc1
 252        0 4395397120 dm-0

```

dm-0 is the group volume

Yet when I look at the size in nautilus is reports:
Volume: 4.5 TB Filesystem
Total capacity: 3.0 TB

The file system on the group volume is ext4

Has anyone have any idea why am I not able to access all the space on the group volume.
And what can I do to solve the issue?

---

### Post by Impavidus on 2013-11-10
4191.78GiB=4191.78*1.024^3=4500.89GB. It's the difference between gigabytes and gigabinarybytes.

GiBs have been invented to get nice numbers for things that often come in powers of 2. Unfortunately it uses non-standard (=non-decimal) conversion factors, making life difficult as long as we humans still count in decimal.

---

### Post by matej.cucek on 2013-11-10
Yeah that would be great if it was just the difference between Gib and GB (TiB & TB). But that's not the case.

The reported free space is only 3TB or  ~2835GB.
At least the byte size should be over 3 500 000 000 B
But as I said it is under 3 000 000 000 B

Currently there is 2.2TB of data on the group volume, and 700GB of free space
I would be more than happy if it reported at least 1.5TB of free space.

---

### Post by steeldriver on 2013-11-10
How exactly did you create/extend the volume group? Did you add the 1.5TB drive as a new PV to an existing VG with an LV/filesystem already in place on the 3TB? The volume group is really just a container (the analog of a 'disk' in non-LVM setups) - you may need to extend the logical volume (the analog of a 'partition') and the actual filesystem as well - see man lvextend and man resize2fs

---

### Post by matej.cucek on 2013-11-10
That's it I extended the LV to the full size but forgot to extend the partition. 
Thanks for the reminder, you were very helpful.

I ran resize2fs and hope this is it.
If I run in more issues I will post a follow up otherwise consider the issue solved.

Thanks a LOT for the help. :)

---


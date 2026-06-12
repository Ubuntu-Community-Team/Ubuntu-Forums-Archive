---
title: "Clone system disk to another disk and boot from it."
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Shellbak3 on 2012-10-25
Ubuntu 11.10
I have an "embedded" computer with an 8 GB internal flash memory disk and am getting out of space errors.  The machine also has a 256 GB disk that is intended to be used for data.  At some point I expect to upgrade the 8GB to 16 GB but that won't happen soon.

I backed up files on the data disk and then used dd to clone the system disk.  I changed the bios to use the data disk as the preferred boot drive but it boots to the 8GB disk.  I'm sure that part of the problem is editing the /etc/fstab file.  I've put what I think are the two relevant lines below where sda1 is the system disk and sdb1 the 256 GB disk:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /media/sdb1 type ext4 (rw,noexec,nosuid,nodev,commit=0,_netdev)

Is it enough to edit /etc/fstab on sdb1 replacing sda1 with sdb1 and sdb1 with sda1?

The system reports that sdb1 is out of space as well so I guess the partition is the same size as sda1.  What can be done to increase the partition size?

I can't make a live CD since the computer has no CD/DVD drive.

TIA, Nate

---

### Post by s1baker on 2012-10-25
I don't know much about it, but some time back I cloned my HD to a larger HD and I wanted to have both of them in the same box, so that I could use the smaller one to use as a backup for important data. I found out that I not only had to edit the fstab file, I had to get a new UUID for one of the HD's ( as they were cloned, thus the same ), and had to apply that new UUID to the HD so that the BIOS would reconize them as being different.

If it helps, here is the post which may or may not help:


[http://ubuntuforums.org/showthread.php?t=1786292]("http://ubuntuforums.org/showthread.php?t=1786292")

---

### Post by shreepads on 2012-10-26
What command did you use to perform the clone?

Was it something like this:
[https://wiki.archlinux.org/index.php/Disk_Cloning#Cloning_an_entire_hard_disk](https://wiki.archlinux.org/index.php/Disk_Cloning#Cloning_an_entire_hard_disk)

IMHO the problem is not /etc/fstab but rather the MBR/ GRUB otherwise the system would at least attempt to boot the bigger drive first...

Can you run Parted on your primary disk and resize the partitions on the data disk?

---

### Post by s1baker on 2012-10-26
I used clonezilla to diskcopy my hard drive.
I cloned a 30 gig HD to a 160 gig HD. The 30 gig
HD was almost full. I ran gparted from an ubuntu .iso
 I had to resize the partition on the 160 cloned HD to allow the full amount of HD to be usuable.
 
 > Can you run Parted on your primary disk and resize the partitions on the data disk?

 If they are on different HD's, I don't know. If the partitions are on the same HD you will have to run gparted from the a ubuntu .iso
 I would recommend using gparted (the graphical version of parted ) instead of parted

---

### Post by Shellbak3 on 2012-10-26
I used
```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

```

It apparently cloned sda with a very large unused un-partitioned portion as expected.

I then installed gparted and attempted to resize sdb1 to 15 GB but there's an error flag that the file system is not recognized and it won't allow me to re-size.  Can't mount it either.

I'd try clonezilla but don't have an optical drive nor a usable thumb drive.  I did see that the UUID of sda1 and sdb1 are identical; again as expected.

---

### Post by shreepads on 2012-10-29
Try this:

a. Create a new label for and re-partition the big drive.

b. Format the primary / partition to ext4 (seems silly but possibly the soure of problems is that SSDs and HDDs mark blank spaces differently)

c. Use the **MBR boot only **and single partition specific dd commands listed in the Arch wiki in my previous post

Also see: [http://blogs.intel.com/technology/2010/08/how_i_switched_to_an_ssd_with/](http://blogs.intel.com/technology/2010/08/how_i_switched_to_an_ssd_with/)

---

### Post by Shellbak3 on 2012-11-01
Still no joy.  The last attempt I used dd_rescue after creating a 14 GB sdb1 partition.  dd_rescue reduced the partition size to that of sda1.  My BIOS/CMOS is set to boot from my big drive.  I edited the fstab file and copied it to sdb1.  It still boots to sda.  I suspect it finds something wrong and defaults to the old boot, there is a file that needs editing, or there is something wrong with sdb's partitioning.

I used boot-repair to get information which is at:
[http://paste.ubuntu.com/1324286/](http://paste.ubuntu.com/1324286/)

sdb1 was hand mounted to /media/sdb1 for access.

Perhaps someone of you can analyze it and give me direction...

---


---
title: "Partitions?"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-08
Hi,

These are my present HDD's partitions.

[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_002-1.png[/IMG]

What are your suggestions & expert views about them.

I was thinking that I should have another 4th FAT32 partition to store backs ups, how should I create that, it's approx size, file system?

Can I use GParted on a live system to resizze these & create another or would I have to used GParted CD for that?

Thanks.

---

### Post by Bucky Ball on 2012-10-08
Resizing must be done booting from a LiveCD if you are intending to resize the / partition as the partition you're manipulating needs to be unmounted. In your case, that is fine. Open Gparted, right click and unmount the partition (sda2). Resize.

I just wonder why you would want to go for FAT32??? Are you wanting to share this with a Win machine? If so, NTFS. If not, EXT4.

PS: sda1 could be half that size as you have a separate /home. 15Gb is usually plenty. To resize that you need to boot from the LiveCD.

PPS: Backups should be done to a different *drive* rather than partition on the same drive, if this is at all possible.

---

### Post by newb85 on 2012-10-08
You cannot resize a partition while it's mounted.  It may be possible to unmount your /home partition while running Ubuntu from the HD, but I wouldn't recommend it.  (There are configuration files in your /home directory that your system uses.)  You should definitely do any resizing using a Live CD or USB.

If you're using MBR (not UEFI), you may want to make sda4 an extended partition and make sda5 the partition for your backups, just in case you want to create a 5th logical partition down the road.

The size will depend on what kind and how many backups you're planning on keeping at a time.  It looks like you have plenty of space, so it's not terribly critical...

Out of curiosity, why would you use FAT32 for your backup partition?  FAT32 has an inherent file size limit, and depending on what kind of backups you're doing, this could be a problem.  Why not stick with ext4?

One thing to keep in mind: while these backups provide some security against data loss, you're still looking at putting them on the same hard drive.  If something happens to the HD, it's all gone...

---

### Post by Bucky Ball on 2012-10-08
@ newb85: Please read all posts. I have mentioned most of this already in the post directly above yours. ;)

---

### Post by Yezinki on 2012-10-08
Thanks for your replies.

I thought back ups can only be stored on FAT32 file system & not ntfs or ext4.

/ should be 25 GB. Primary ext4

/home 144. Primary ext4.

swap. Primary 4 GB.

/ Extended > Logical for back ups 50-80 GB?

---

### Post by Bucky Ball on 2012-10-08
Fine. You also don't really need more than 2Gb /swap unless you hibernate with heaps of apps and other things open/running.

---

### Post by newb85 on 2012-10-08
> **Bucky Ball said:**
> @ newb85: Please read all posts. I have mentioned most of this already in the post directly above yours. ;)

When I started composing my post, yours wasn't up yet.  I was distracted halfway through writing mine, hence the time lag...

---

### Post by newb85 on 2012-10-08
> **Bucky Ball said:**
> Fine. You also don't really need more than 2Gb /swap unless you hibernate with heaps of apps and other things open/running.

That was probably automatically set up during install to reflect the amount of RAM available.  Is it really worth changing to gain 2GB of HD space amidst that vast sea of unused bits?

---

### Post by vasa1 on 2012-10-08
> **newb85 said:**
> When I started composing my post, yours wasn't up yet.  I was distracted halfway through writing mine, hence the time lag...

Sometimes, the forum "hangs". That also could result, unintentionally, in posts with very similar content.

---

### Post by Bucky Ball on 2012-10-08
> **newb85 said:**
>  Is it really worth changing to gain 2GB of HD space amidst that vast sea of unused bits?

No.

---

### Post by audiomick on 2012-10-09
> **Yezinki said:**
> Thanks for your replies.

I thought back ups can only be stored on FAT32 file system & not ntfs or ext4.

/ should be 25 GB. Primary ext4

/home 144. Primary ext4.

swap. Primary 4 GB.

/ Extended > Logical for back ups 50-80 GB?


Yes, do make the new partition a logical in an extended partition. There is no reason I know of not to, and if you do, it leaves the way open to more easily add more partitions if you should want to at any time in the future.

A word on file systems: NTFS is a good idea if you want a parition to be accessible from a windows install. If, however, you are definitely only going to be accessing from a Linux system, then stick to the Linux file systems such as Ext4. If nothing else, Linux permissions don't work on NTFS partitions. Also, Linux file systems generally don't need defragmentation whereas an NTFS partition likely will eventually even if you are accessing it only form Linux.

> **Bucky Ball said:**
> No.
My thoughts exactly. If you are not desperately short of space, leave the swap as it is.

---

### Post by Yezinki on 2012-10-10
Thanks for replying.

I don't intend a dual boot with windows, so an extended/logical ntfs is out, can a ext4 file system partition store/restore back ups?

---

### Post by oldos2er on 2012-10-10
Backups are just data on a disk, same as any other data. If you're only going to be using Linux, use a Linux file system, FAT32 does not support Linux permissions.

---

### Post by Yezinki on 2012-10-11
Thanks.

---


---
title: "Hard drives changed sdx designations... should I be worried?"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by akiratheoni on 2012-12-30
Previously my hard drive setup was like this:

/dev/sda - Windows partition, has sda1 and sda2
/dev/sdb - Ubuntu partition, has sdb1, sdb2, sdb5, sdb6, sdb7; no idea why they skipped sdb3 and sdb4

/dev/sdc - External drive. Backups and files and stuff. Has sdc1 only.

But now, I found that the computer didn't recognize the External drive.

sudo fdisk -l revealed that:

/dev/sda (Windows) was now /dev/sdf (with sdf1 and sdf2)
/dev/sdb (Ubuntu) was now /dev/sdg (with sdg1, sdg2, sdg5, sdg6, sdg7)

The partition numbers are the same; the new partition numbers for the Ubuntu drive still skipped 3 and 4.

... and once I got the external drive recognized again, my external drive /dev/sdc was now **/dev/sda**, with the partition being /dev/sda1.

Is this a cause for alarm? Might my computer write over data in /dev/sda1? I will disconnect my external hard drive before I shut down this computer just in case but... it's kind of weird.

---

### Post by Wim Sturkenboom on 2012-12-30
Unless you have a non-standard setup, sda/sdb etc are no longer used, at least not when the system is running.

If you run _cat /etc/fstab_, you will see that partitions are mounted by UUID and not by device; UUIDs are unique for each partition.
```

wim@aa0:~$ **[COLOR="Red"]cat /etc/fstab[/COLOR]**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
[COLOR="Red"]UUID=4e8c9e38-845f-435a-b24a-ef8c37cba4a2[/COLOR] /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
[COLOR="Red"]UUID=ef260aa3-f22f-4730-8517-8546c15cba30[/COLOR] none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0
wim@aa0:~$

```
The same applies when you insert a memory stick or pendrive. If they have a label, that will be used, else the UUID will be used. You can see it when it's connected by running _ls /media_ in a terminal; you will see e.g. /media/pendrive (label of the memory stick is 'pendrive') or /media/longnumber (UUID).
So under Linux, I would not be worried. If you manually (or using your own scripts) mount by device, the story will be different!

I'm not sure what Windows does but if you can still see everything as expected, there is no reason for concern.

---

### Post by arpanaut on 2012-12-30
I have a mix of pata, sata drives in one of my rigs and get this changing behavior.
I also see this if I have a card reader or USB hub attached.
Yes it's disconcerting at times, I try to not boot with them attached and to mount later to avoid drives getting skewed.

I had big problems with grub before uuid's was implemented for booting, but I always check what my system is seeing as drive designations before I do any command line operations re: writing to drives and partitions.  
Pay attention and you should be okay.

---

### Post by akiratheoni on 2012-12-30
> **Wim Sturkenboom said:**
> Unless you have a non-standard setup, sda/sdb etc are no longer used, at least not when the system is running.

If you run _cat /etc/fstab_, you will see that partitions are mounted by UUID and not by device; UUIDs are unique for each partition.
```

wim@aa0:~$ **[COLOR="Red"]cat /etc/fstab[/COLOR]**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
[COLOR="Red"]UUID=4e8c9e38-845f-435a-b24a-ef8c37cba4a2[/COLOR] /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
[COLOR="Red"]UUID=ef260aa3-f22f-4730-8517-8546c15cba30[/COLOR] none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0
wim@aa0:~$

```
The same applies when you insert a memory stick or pendrive. If they have a label, that will be used, else the UUID will be used. You can see it when it's connected by running _ls /media_ in a terminal; you will see e.g. /media/pendrive (label of the memory stick is 'pendrive') or /media/longnumber (UUID).
So under Linux, I would not be worried. If you manually (or using your own scripts) mount by device, the story will be different!

I'm not sure what Windows does but if you can still see everything as expected, there is no reason for concern.

Thanks so much for the answer. I haven't used Ubuntu lately, so it's my first time using Ubuntu in a long time, and I wasn't aware of the UUID change. It looks like that my /etc/fstab all mount though UUID and not the /dev/sdx way, so I think I'll be OK. Thanks!

---

### Post by deadflowr on 2012-12-31
> /dev/sdb - Ubuntu partition, has sdb1, sdb2, sdb5, sdb6, sdb7; no idea why they skipped sdb3 and sdb4

From the looks it seems you have one primary partition and one extended partition(sdb1 and sdb2).
Typically, 1,2,3,4 are designated for primary partitions(extended are primary) and 5 and up for logical partitions.
It's normal to set it up like this and see the 3rd, and 4th not listed.

---

### Post by akiratheoni on 2012-12-31
> **deadflowr said:**
> From the looks it seems you have one primary partition and one extended partition(sdb1 and sdb2).
Typically, 1,2,3,4 are designated for primary partitions(extended are primary) and 5 and up for logical partitions.
It's normal to set it up like this and see the 3rd, and 4th not listed.

OK now that you mention the primary and logical partitions, I'm pretty sure that's what it did. As I said earlier I haven't used Ubuntu in awhile (I installed this Ubuntu 12.04 back in May and haven't really used it since) so I forgot about the primary/logical thing. So that explains it! Thanks.

---


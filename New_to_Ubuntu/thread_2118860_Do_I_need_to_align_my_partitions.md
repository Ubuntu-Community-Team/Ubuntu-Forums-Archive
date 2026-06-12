---
title: "Do I need to align my partitions"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by jostar on 2013-02-22
Finally got my HP N40L up and running with 250Gb OS drive and 2x2TB as RAID 1 for data.

Started filling the drives and notice it's kinda slow suppose to be 4hrs for about 120Gb, didn't wait for it to finish and went to bed. I'm not sure if it's because I'm copying from the laptop over wifi. Saw some mention of HDD needs to be aligned especially SSD. Do I need to do that with a normal drive?

This is what I get with parted -l
```
Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid


Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid


Model: ATA VB0250EAVER (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   250GB  250GB  extended
 5      257MB   250GB  250GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 243GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  243GB  243GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 6304MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  6304MB  6304MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext3

```

---

### Post by thermion on 2013-02-22
If you are really transfering files via wifi, than that's your bottleneck right here.

---

### Post by CharlesA on 2013-02-22
> **thermion said:**
> If you are really transfering files via wifi, than that's your bottleneck right here.
+1. If I have a lot of data to transfer to my laptop, I connect via ethernet.

@OP: This should answer your question:
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

The use of wifi is likely the cause of the slow speed.

---

### Post by jostar on 2013-02-22
Thank you for the replies, I am aware that the use of Wifi is the bottleneck, also the fact that RAID 1 have a lower write speed by nature.

I think to clarify things, what I should have said is that I stumble upon this thing about partition alignment which I have never heard of before. I did some reading and I can understand bits and pieces of it, but not fully. My question: Is it critical to have the partitions aligned? And if so, how to do that?

---

### Post by CharlesA on 2013-02-22
You do it when you create the partitions. Gparted automatically aligns any partitions it creates to 1MiB.

---

### Post by jostar on 2013-02-23
So based on the output from my OP, do I need to do anything?

Gparted won't reckonise the RAID in the graphic interface. It can see the drives in an array but it says unknown under file system...
That's a whole different discussion I had previously, which have been resolved / ignored
[http://ubuntuforums.org/showthread.php?p=12524111#post12524111](http://ubuntuforums.org/showthread.php?p=12524111#post12524111)

I've found the source of the slow transfer speed. I've checked the LAN LED on the Netgear router, it's in amber which mean the connection is in 10Mbps... That's whole another problem to solve.

---

### Post by CharlesA on 2013-02-23
Well, you formatted the drives using 512byte sectors when the drives themselves use 4096 byte sectors. I don't know if that has any performance impact, but it likely does.

---

### Post by jostar on 2013-02-23
Sorry to keep on asking newbie questions...

So there are 2 side of the alignment issue:
1. My drives are currently formatted with 512 bytes sector rather than 4096 bytes sector.
2. The partition starts at 0 without any free space in front

How do I go about fixing them?

So I reformat the drive with the following that should give me the correct sector size, how about the start position?
mkfs.ext3 /dev/md1 -b 4096

---

### Post by CharlesA on 2013-02-23
Not sure, it might be just the drive itself. I have an external drive that is like that.

See here: [https://wiki.archlinux.org/index.php/Advanced_Format](https://wiki.archlinux.org/index.php/Advanced_Format)

---

### Post by jostar on 2013-02-23
Thanks,

Read through the post and the link, it seems that there is nothing that I need to worry about.

[https://www.tolaris.com/2011/07/21/libblkid-or-why-you-dont-need-to-worry-about-4k-disk-format/](https://www.tolaris.com/2011/07/21/libblkid-or-why-you-dont-need-to-worry-about-4k-disk-format/)

---


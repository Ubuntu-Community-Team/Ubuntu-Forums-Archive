---
title: "Partion madness"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by slashdog on 2008-10-06
Well i finally gave up on dual boot. YAY UBUNTU WON!

I was wondering if this is a normal disk structure. It seems to me that i have two partitions overlapping :confused:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15630683

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       24321   156296385    5  Extended
/dev/sda5           23956       24321     2939863+  82  Linux swap / Solaris
/dev/sda6            4864       23955   153356427   83  Linux

Thanks for your help!

---

### Post by zvacet on 2008-10-06
From just look in your partition table it look that you don´t have Windows partition.Am I wrong?

---

### Post by Greyed on 2008-10-06
> **slashdog said:**
> I was wondering if this is a normal disk structure. It seems to me that i have two partitions overlapping :confused:

Would help if you explained why you thought that.

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       24321   156296385    5  Extended
/dev/sda5           23956       24321     2939863+  82  Linux swap / Solaris
/dev/sda6            4864       23955   153356427   83  Linux

```

I presume you mean sda2 & sda5/sda6 being on the same area?

sda2 is an extended partition.  Extended contain logical partitions.  Or, to put it another way, you couldn't have sda5 and sda6 without first having sda2 there to contain them.  That is normal.

Read the porting about primary, logical and extended partitions here:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by kansasnoob on 2008-10-06
> **Greyed said:**
> Would help if you explained why you thought that.

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       24321   156296385    5  Extended
/dev/sda5           23956       24321     2939863+  82  Linux swap / Solaris
/dev/sda6            4864       23955   153356427   83  Linux

```

I presume you mean sda2 & sda5/sda6 being on the same area?

sda2 is an extended partition.  Extended contain logical partitions.  Or, to put it another way, you couldn't have sda5 and sda6 without first having sda2 there to contain them.  That is normal.

Read the porting about primary, logical and extended partitions here:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Exactly right!

Look here:

[ATTACH]87465[/ATTACH]

You see I have one primary partition and everything else is contained in one extended partition!

---

### Post by Liviu-Theodor on 2008-10-06
I saw your image. If you would have tried to do this *only* with primary partitions, you would have run into problems, because a HDD can have only up to four primary partitions. And Linux can be installed in a logical partition, unlike Windows. And an extended partition can include any number of logical partitions, but must be contiguous.

---

### Post by tubasoldier on 2008-10-06
Your partition table looks correct to me.
However, your swap space is redundant. You only need one swap. Your operating system will really only utilize one of them. And all of the operating systems you have installed will use the same one.

---

### Post by Greyed on 2008-10-06
> **tubasoldier said:**
> Your partition table looks correct to me.
However, your swapspace is redundant.

How do you figure?  He's only got a single swap partition.

---

### Post by tubasoldier on 2008-10-06
> **Greyed said:**
> How do you figure?  He's only got a single swap partition.

I guess I should pay closer attention to who I am responding to.
Kansasnoob has two swap partitions in the picture he posted.

sorry for my confusion.

---

### Post by slashdog on 2008-10-06
thanks all for your help! Problem sorted

---


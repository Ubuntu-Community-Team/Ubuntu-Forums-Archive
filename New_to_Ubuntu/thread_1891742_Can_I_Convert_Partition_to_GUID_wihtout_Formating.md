---
title: "Can I Convert Partition to GUID wihtout Formating ?"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by begin on 2011-12-06
and another Question 
Is Formating format all hard drive or just the partition ?

---

### Post by westie457 on 2011-12-06
Hi to answer the main question. Changing the partition table to a different style EG - MBR to GPT or just rewriting it will effectively wipe the hard drive of all information.

In answer to the second question formatting is usually applied to a partition even if there is only one partition on the drive.

---

### Post by BC59 on 2011-12-06
I agree with westie457 even not understanding well the first question. Any change of the status of a partition is practically wiping out all data.
To the other question, the answer is that partitioning a HDD, is like creating different HDDs. So formatting a partition, doesn't affect the other ones.

---

### Post by begin on 2011-12-06
Thanks
Now When Use Disk Utility It Just Want to Format all The Hard drive

---

### Post by BC59 on 2011-12-06
> **begin said:**
> Thanks
Now When Use Disk Utility It Just Want to Format all The Hard drive

The better and sometimes the only way to deal with partitions is booting from a Live CD and then using the tool GParted.
It's the only way because to make changes the partition should be unmounted.

---

### Post by coffeecat on 2011-12-06
@begin, you can in fact convert a MBR partition table to a GUID partition table without data loss using gdisk, but I wouldn't recommend a beginner doing this. See:

[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

And:

[http://www.rodsbooks.com/gdisk/whygdisk.html](http://www.rodsbooks.com/gdisk/whygdisk.html)

> You want to convert an MBR disk to GPT format without data loss. GPT fdisk permits doing this, although doing so will require you to re-install your boot loader (if it's a boot disk).*** Do not attempt to convert a Windows boot disk from MBR to GPT form unless you're an expert!***

---

### Post by begin on 2011-12-06
I mean when you want to convert your partition as GUID The only way to make Disk Utility offer This option is when you want to Format all hard drive 
And Gparted Don't offer this when try to format it or make new one

---

### Post by coffeecat on 2011-12-06
@begin, a partition isn't GUID. A partition table is GUID or MBR (or some other types). What is it that you are wanting to achieve?

---

### Post by begin on 2011-12-06
Thanks
I will use GPT fdisk Carefully

---

### Post by coffeecat on 2011-12-06
I posted that link only as a for-the-record. I really do not recommend that you try converting your partition table to GPT unless you have very, very good reasons so to do. You didn't answer my question: what are you trying to achieve? There may be easier and better ways around whatever issue you have. If you proceed with converting your partition table, read all that link, **all** the pages, and do so at your own risk. If you do proceed, I can help you no further.

---

### Post by begin on 2011-12-06
I Want it to get recognized in Installation for Multi boot OS

 it is not a problem for me to format the partition but I have a problem in formating  all hard drive

---

### Post by begin on 2011-12-06
Is there a Program that Format the partition and make it GUID ?

---

### Post by westie457 on 2011-12-06
@begin
When using Gparted as already stated use from a LiveCD Desktop the only way Gparted will format the whole drive is when there is only one partition. Otherwise you have to go to the Menu options at the top of the Gparted window and select Device > Create New Partition Table (the quick way) or delete partitions one at a time until there are none left then click New and choose how it is to be formatted.

@coffeecat
was not aware the conversion could be done at all. However that is something I will not be trying as I am not that brave and certainly not an expert.

---

### Post by begin on 2011-12-06
I did what you said and this message appear
[IMG]http://img15.imageshack.us/img15/8243/screenshotat20111206151.png[/IMG]

---

### Post by N00b-un-2 on 2011-12-06
I'm assuming you're starting from MBR.  Unfortunately, there is not really any way to convert an MBR disk to GUID without reformatting.  If your hard drive is partitioned as a GUID device, the opposite is --kind of-- true.  GUID has the ability to emulate an MBR, but is limited by the fact that MBR can only support four primary partitions.  This becomes very limiting when taken into consideration that a typical GUID drive will have a small hidden partition as the first partition, typically 40-100mb which is intended to store EFI information.  Essentially, this leaves you with only three usable MBR partitions.

Curious that you would want to use GUID since only intel itanium servers and Macs use this standard.  If you're trying to hackintosh, I would highly recommend you patch your install DVD to allow it to install on MBR.  It's very easy to do.  Link to my blog about it [http://n00b-un-2.blogspot.com/2011/08/how-to-create-snow-leopard-usb.html]("http://n00b-un-2.blogspot.com/2011/08/how-to-create-snow-leopard-usb.html") Scroll down to the section about preparing for MBR install

---

### Post by westie457 on 2011-12-06
**Do Not Click** 'Apply' unless you want to wipe the hard drive.

All information will be lost with very little to no chance of recovering any of it. Unless you have everything backed up to somewhere safe EG an external hard drive **_Do Not Click the APPLY button_**

---

### Post by Elfy on 2011-12-06
The post referring to hackintosh has been removed.

If this thread is in fact about getting hackintosh working the thread will be jailed.

---

### Post by begin on 2011-12-06
So there is no way with Gparted

---

### Post by N00b-un-2 on 2011-12-06
why would you block the thread simply because I asked why wanted to partition his hard drive as GUID.  I simply stated that the only computers that use GUID are intel itanium servers and Macs and I would strongly advise against partitioning as GUID unless you have a good reason for it, since, as the OP stated it is to get a multiboot system installed.  Windows does not play very well on GUID partitions unless you're on a real Mac and using Boot Camp.

---

### Post by N00b-un-2 on 2011-12-06
> So there is no way with Gparted

No, there is no way to convert to GUID from MBR without formatting your hard drive.  GParted will very easily do the conversion for you, but like I said -- ESPECIALLY if you plan on trying to install Windows on your computer alongside Ubuntu or any other OS I would highly recommend you don't attempt to do this as you're going to run into headaches.  If you're trying to install "some other" OS, there are ways to do so on MBR drives.

---

### Post by begin on 2011-12-06
Thanks ;)

---

### Post by lisati on 2011-12-06
> **N00b-un-2 said:**
> why would you block the thread simply because I asked why wanted to partition his hard drive as GUID.
We don't support circumventing EULAs here. Please see [http://ubuntuforums.org/showpost.php?p=11517587&postcount=16](http://ubuntuforums.org/showpost.php?p=11517587&postcount=16)

---


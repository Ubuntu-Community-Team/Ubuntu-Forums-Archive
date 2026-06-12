---
title: "External HDD"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Darkhaund on 2012-08-21
I was wondering if any HDD drive will work on either my lununtu laptop, my ubuntu destkop and my home windows 7 file

I basically want to store pictures and work stuff on the HDD and use it while at home and at work bringing it back and forth.

Any restrictions or any external HDD drive will work just fine

Thanks in advance

---

### Post by anewguy on 2012-08-21
> **Darkhaund said:**
> I was wondering if any HDD drive will work on either my lununtu laptop, my ubuntu destkop and my home windows 7 file

I basically want to store pictures and work stuff on the HDD and use it while at home and at work bringing it back and forth.

Any restrictions or any external HDD drive will work just fine

Thanks in advance

Use a USB drive.  If the disk is ntfs you should be fine.  You can read/write ntfs with linux or Windows (obviously) but trying to do the same from Windows to a linux partition is possible, but I wouldn't recommend it - just me personally.  It's already a proven matter the first way.

What I'm unfamiliar with, and somebody may be able to help with, is whether or not you'll have to mount the disk to ubuntu or lubuntu.  I suspect not, as I can't see any difference between that and other USB devices I have used as disks.

---

### Post by Darkhaund on 2012-08-21
I see...

basically i want or get a 500 GB or a 1 TB extral USD HDD that i can easily read on my ubuntu machies and my windows  7 machine

---

### Post by c_cinq on 2012-08-21
format the hdd as ntfs or vfat, then ubuntu and windows will be able to read.  of course, you need to have ntfs-3g installed on ubuntu, to read and write on a ntfs partition.

---

### Post by Darkhaund on 2012-08-21
Does ubuntu 12.04 lts come with that package installed or do i have to install it myself?

---

### Post by era86 on 2012-08-21
Something that bit me in the butt while configuring my external HD for Windows, Mac, and Ubuntu was the 4GB limit on files on partitions formatted to FAT32. I wrote about it [here]("http://runtime-era.blogspot.com/2012/01/zero-and-format-external-hard-drive.html").

I would recommend NTFS if you need to share between these three platforms.

---

### Post by Paqman on 2012-08-21
> **Darkhaund said:**
> Does ubuntu 12.04 lts come with that package installed or do i have to install it myself?

It's been part of the default install for years now, I'm surprised to even see it mentioned tbh.

+1 for using NTFS, FAT is an old filesystem with some quite annoying restrictions.

---

### Post by newb85 on 2012-08-21
I run a 1TB USB HDD that came pre-formatted as NTFS.  It's plug-and-play in Ubuntu--nothing to install.  It behaves much the same as a flash drive, although the name and icon Ubuntu give it show that it knows the difference.  I've been happily using it with Deja Dup for some time.

Ubuntu's support for NTFS is superb, so there's no reason to use FAT32.  I've never tried to access an EXT# filesystem from Windows, but I can't imagine it's any fun.  (Of course, my blood pressure begins to rise every time I boot into Windows, anyways.  ;))

---

### Post by Darkhaund on 2012-08-22
so.. i just buy ANY external HDD and make suer it is in NTFS or format it on that format?

---

### Post by anewguy on 2012-08-22
That's pretty much it.  Some drives have their own external power supplies.  Others use USB for the power (often with a double-plug USB cable).  Be sure to get USB, and get the fastest version of USB that will run with all your computers - I would suspect this will be USB 2.0 or 2.1, but check you specs just to be sure.

The drive may already come partitioned and formatted.  Be sure to check that so that you do make it ntfs.

---

### Post by Darkhaund on 2012-08-22
Once i get the HDD ill let you know what happens. Ill be back on this thread in a few days

---

### Post by anewguy on 2012-08-22
Good luck, and I'm sure everything will work just great.  Everyone who has helped here will be waiting to hear the good news!

---


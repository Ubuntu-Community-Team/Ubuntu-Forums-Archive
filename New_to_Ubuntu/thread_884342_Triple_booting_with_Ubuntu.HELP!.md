---
title: "Triple booting with Ubuntu.HELP!"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by ginaw4eva on 2008-08-08
Hi.:) I'm new to using Ubuntu..actually Linux in general. A friend told me abt how he loves it and I couldn't help but investigate it. I got Ubuntu 8.04. I tried it out from the CD and I loved it. I want to install it now. 

I have 2 OS installed and I want to keep them. I did a little research as to how I can install Ubuntu within affecting my Windows OSs.

I found 2 methods and I not sure which i should do. Plus I'm not that clear on how to do them.

Method one. You run Ubuntu from the CD > Click Install > click on the Install Icon> Manual Install > Resize Drive > Do something like a swap drive >  create new partition > check logical/beginning/ext3 > mount point:/ >Advance:check bootloader.

Method 2: Start Windows > Insert CD > Install like an application. I dont have anymore info in this cos most said it was straight forward.


Here's what I want. I want my 2 Windows OS to remain as it is. I have 4 partitions. I cleared out 1 Partition for this purpose but If I can ... and I think it is possible... I want to install it on 1 of the partitions that I have Windows installed. Because I really wanted to use the free space partition just to store files that I can easily access no matter which OS I'm on.

Advice anyone:confused:

---

### Post by cdtech on 2008-08-08
The install will ask you which partition you want to install to. The GRUB Bootloader will be installed on the MBR of the primary drive only if you prefer it to be installed there.

Hope this helps.......

---

### Post by caljohnsmith on 2008-08-08
> **ginaw4eva said:**
> I have 4 partitions. I cleared out 1 Partition for this purpose but If I can ... and I think it is possible... I want to install it on 1 of the partitions that I have Windows installed. Because I really wanted to use the free space partition just to store files that I can easily access no matter which OS I'm on.

Advice anyone:confused:

You can install Ubuntu over the Windows partition if you want, but keep in mind that Ubuntu actually needs at least two partitions: one for the OS and one for its swap space. If you all ready have 4 primary partitions on your HDD, you can't create any more primary partitions since the max is 4. Therefore you would have to convert the partition you want to install Ubuntu into to an "extended" partition, where within that you create two "logical" partitions (one for Ubuntu, one for swap space). In other words, the extended partition is really just a enclosure or wrapper around the two logical partitions you would create in it. And you can have about as many logical partitions as you want.

That may sound a bit complicated, but it really isn't if you do it with Ubuntu's partition editor (gparted) that is part of the install process. It graphically shows you what your partitions look like, and it is easy to manipulate. Just be REALLY careful that you know for sure what is what so you don't overwrite a partition you didn't mean to.

By the way, welcome to the forums. :)

---


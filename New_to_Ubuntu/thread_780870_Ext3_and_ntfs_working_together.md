---
title: "Ext3 and ntfs working together?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by StaticIp on 2008-05-03
[SIZE="3"]I am using a 250gig external to run Ubuntu 8.04, I set aside 10 gigs for my Ubuntu ext3 partition, 1 gig for the swap and the rest is ntfs for transferring between windows and Ubuntu. I use portable applications from [here]("http://portableapps.com") and I use a lot of the same application in windows and on Linux. I didn't want to use wine to run my applications since I have more stable version designed for Ubuntu. So i was wondering if the application roots (where they store their settings and data) could be changed to the same one? So if I would boot into windows and use my portable apps they could pull the settings from the Ubuntu partition or the other way around. So I don't have to manage both at once, just set one and the data is saved in the same directory and all apps have the same settings under Ubuntu and windows. Or is their a way to just automatically sync the settings and data?[/SIZE]

---

### Post by Oldsoldier2003 on 2008-05-03
If the application allows sharing of the configurations and data it shouldn't be a problem. One provision though- NTFS doesn't support full permissions the way Linux does so you might experience some issues. Then again you might not :)

My thought would be to store the shared data on the shared usage partition and to leave the configurations with the application.

---

### Post by glennric on 2008-05-03
The easiest way would be to put the application roots on the ntfs partition.  You can mount ntfs partitions with read/write access in ubuntu quite easily.  I recommend ntfs-3g, but the fuse module works as well.

It can be done the other way around (put the files on an ext3 partitions), for instance with ext2fsd.

---

### Post by Oldsoldier2003 on 2008-05-03
> **glennric said:**
> The easiest way would be to put the application roots on the ntfs partition.  You can mount ntfs partitions with read/write access in ubuntu quite easily.  I recommend ntfs-3g, but the fuse module works as well.

It can be done the other way around (put the files on an ext3 partitions), for instance with ext2fsd.

True. The only issue i can see is that either way permissions will not work correctly for the portable application. Depending on the application this could very well be meaningless, its something that the OP will have to try out with non critical data.

---

### Post by StaticIp on 2008-05-03
How would I go about setting permission? If the partitons are on the same drive shouldn't it already have them? Say I have pidgin running in ubuntu and have it call the userlist settings, ect.. from the ntfs pidgin folder. If I am able to mount the ntfs partition wouldnt I have permission? How would I change where pidgin called the information from? Oh and thankyou for the quick replies!

---

### Post by iSplicer on 2008-05-03
The best solution would be to allocate a large FAT32 *dump* partition that both linux and windows can conveniently write to without any issues.

---


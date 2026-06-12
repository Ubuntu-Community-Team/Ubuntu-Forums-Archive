---
title: "Why Does New Install Not Create a Bootable HD?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by HDTimeshifter on 2008-10-14
I installed 8.04 on a newly built system with no OS and after removing the CD and rebooting, it always says "CD-ROM Boot Priority ..No Medium" and won't boot from the hard drive, but only from the CD.  Why doesn't the default install create a non-live boot?  How do I install it so that it won't require a CD to boot?  You would think the default would be to create a non-live system.  This is very un-intuitive for a new Ubuntu user.  Also during the installation, it failed on the default "Guided partition" (1st option), saying disk size too small (on a 698 GB partition???), so I had to pick the 2nd option Guided partition (use entire disk 750GB).

---

### Post by HDTimeshifter on 2008-10-14
I installed 8.04 on a newly built system with no OS and after removing the CD and rebooting, it always says "CD-ROM Boot Priority ..No Medium" and won't boot from the hard drive, but only from the CD. Why doesn't the default install create a non-live boot? How do I install it so that it won't require a CD to boot? You would think the default would be to create a non-live system. This is very un-intuitive for a new Ubuntu user. Also during the installation, it failed on the default "Guided partition" (1st option), saying disk size too small (on a 698 GB partition???), so I had to pick the 2nd option Guided partition (use entire disk 750GB).

(Sorry about the cross post, but I haven't gotten a response in the 64-bit thread.  I did an install with 64-bit Ubuntu.)

---

### Post by overdrank on 2008-10-14
Hi and welcome, no answers in 15 mins? Please do not create multiple threads on the same issue.
As for your issue was there a error installing the grub? DO you see a grub loading screen after the system post?
Moved to ABT :)

---

### Post by Patb on 2008-10-14
HD, welcome to the forum. Your simplest option might be to reinstall and choose the manual partitioning option. That way you see clearly the partition setup before committing anything. Make sure you set it so that the root partition has the boot flag. 

If you want to try to get your existing installation going, please open a terminal and post the output of:
```
sudo fdisk -l
```

Cheers, Pat.

---

### Post by trikster_x on 2008-10-14
I would check your bios and make sure that your computer is setup to boot an hdd first. Ubuntu does have a bootloader, its called grub.  It will display all bootable options on startup if you don't have a boot disk in your chosen first boot drive.  If you get into your BIOS and everything is fine, then there may have been an error when your liveCD tried to install grub, or you could have a bad liveCD.  Just try to reinstall and if that doesn't work, you probably need a new liveCD.

---

### Post by HDTimeshifter on 2008-10-14
> **overdrank said:**
> Hi and welcome, no answers in 15 mins? Please do not create multiple threads on the same issue.
As for your issue was there a error installing the grub? DO you see a grub loading screen after the system post?
Moved to ABT :)

I hate to cross post, but no replies in the other forum for 20 min, that's why I posted here.  I'm not sure what the grub loading screen is supposed to look like since this is my first time installing any Linux, but I didn't get any errors (other than the partition choice) and it seemed to install ok.

---

### Post by HDTimeshifter on 2008-10-14
> **Patb said:**
> HD, welcome to the forum. Your simplest option might be to reinstall and choose the manual partitioning option. That way you see clearly the partition setup before committing anything. Make sure you set it so that the root partition has the boot flag. 

If you want to try to get your existing installation going, please open a terminal and post the output of:
```
sudo fdisk -l
```

Cheers, Pat.

What settings and sizes should I use for manual partitioning?  Since this is my first time every installing a Linux, I have no idea what to use - you'd think the guided install would select defaults.

---

### Post by trikster_x on 2008-10-14
The guided install does select defaults.  The only benefit of a manual install comes when you understand what a swap partition is and want to make it the best size for your system.  I believe guided install only partitions 512MB for a swap.  In any case it is extremely unlikely it has anything to do with guided install. If you are starting with a fresh HDD and don't plan on using windows then just leave the entire HDD with Ubuntu.  If you plan on using windows, then just make sure you leave at least 40 GB on your HDD, preferably at the beginning.  The main part of your HDD should have the extension "/" and there should be a swap parition that is at least 512 MB, but you can set it where ever you want.  This is a pretty good guide for partitioning your drive:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by HDTimeshifter on 2008-10-15
> **trikster_x said:**
> I would check your bios and make sure that your computer is setup to boot an hdd first. Ubuntu does have a bootloader, its called grub.  It will display all bootable options on startup if you don't have a boot disk in your chosen first boot drive.  If you get into your BIOS and everything is fine, then there may have been an error when your liveCD tried to install grub, or you could have a bad liveCD.  Just try to reinstall and if that doesn't work, you probably need a new liveCD.

Isn't the purpose of setting removable drives first so you can override the hard drive boot if necessary?  I thought if there is nothing in the 1st boot choice, the system will go to the next, and so forth until it finds a bootable device.  Well, I just moved the HD first, and that fixed it.  That is the reverse of how all PCs have been set up in the past, again counter-intuitive.

---

### Post by trikster_x on 2008-10-15
I should clarify what I meant.  I meant that the first thing you should do is check your bios to make sure that it was setup to read your HDD.  If your BIOS does not have your HDD set as a boot device at all, then it does not boot by default.  You obviously have the problem fixed, now try putting the HDD as the second boot device and your CDrom as the first.  If that is what your setup originally was, then I would say your BIOS is messed up.  Your BIOS settings have nothing to do with ANY OS.  They are software written on individual chips on your motherbard that tell your components how they should work.  Until one of your boot devices begins to load your computer's operation has nothing to do with your OS.

---

### Post by jerome1232 on 2008-10-15
> **HDTimeshifter said:**
> Isn't the purpose of setting removable drives first so you can override the hard drive boot if necessary?  I thought if there is nothing in the 1st boot choice, the system will go to the next, and so forth until it finds a bootable device.  Well, I just moved the HD first, and that fixed it.  That is the reverse of how all PCs have been set up in the past, again counter-intuitive.

Out of pure curiosity whose the manufacturer of your BIOS, that is an odd factory default setting if you ask me.

Then again one computer I bought was configured to boot via pxe (over the network) by default.

---


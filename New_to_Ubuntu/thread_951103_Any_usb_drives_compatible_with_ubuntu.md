---
title: "Any usb drives compatible with ubuntu?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by J03y on 2008-10-17
Are there any usb flash drives that are compatible with ubuntu?

---

### Post by zamadatix on 2008-10-17
we installed ubuntu on  external and although i havent done it on my flash i imagine it would work the exact same way. though ive been playing around with portable os's for your flash drive and pendrivelinux2008 is probably the best for a 2gb or smaller drive (untill you get to 256mb then use puppy or dsl)

---

### Post by SunnyRabbiera on 2008-10-17
Like external hard drives and such?
Seagate is known to work a good percentage of the time, as is Western Digital.

---

### Post by jerome1232 on 2008-10-17
Unless they require to install some driver under Windows they are pretty much just hard drives and work just like any other hard drive.

There are some that have problems (they'll spin themselves down or something like that and Ubuntu doesn't like it)

---

### Post by J03y on 2008-10-17
> **jerome1232 said:**
> Unless they require to install some driver under Windows they are pretty much just hard drives and work just like any other hard drive.

There are some that have problems (they'll spin themselves down or something like that and Ubuntu doesn't like it)Is San Disk with U3 compatible with ubuntu?

---

### Post by SunnyRabbiera on 2008-10-17
> **J03y said:**
> Is San Disk with U3 compatible with ubuntu?

San Disk has a reputation of being Linux friendly, its worth a shot.

---

### Post by jerome1232 on 2008-10-17
I remember helping someone on these forums with a scan disk that had u3 on it, so yes (he was asking about formating it)

u3 is a program that lets you store your windows settings on it right? the u3 won't work under Ubuntu but the thing will function as a usb disk fine.

---

### Post by Therion on 2008-10-17
My Kingston DataTraveler works like a charm...  8GB and ~$20 on NewEgg.  
But then really just about ANY USB thumb drive should work on Ubuntu.

---

### Post by damis648 on 2008-10-17
If they use a standard USB Mass Storage as the interface and driver in windows the the drive will have a chance of 99.99% of working in Ubuntu.

---

### Post by J03y on 2008-10-17
> **SunnyRabbiera said:**
> San Disk has a reputation of being Linux friendly, its worth a shot.Nope, I just ran the CD that's supposed to be U3 but it just took it as a regular CD.

---

### Post by J03y on 2008-10-17
> **jerome1232 said:**
> I remember helping someone on these forums with a scan disk that had u3 on it, so yes (he was asking about formating it)

u3 is a program that lets you store your windows settings on it right? the u3 won't work under Ubuntu but the thing will function as a usb disk fine.When I insert my San Disk it always says, "Unable to mount media. There is probably no media in the drive".

---

### Post by jerome1232 on 2008-10-17
Is ithis a cd-rom your talking about? Like I said the u3 software won't work inside ubuntu, the usb sticks will work as normal though.

---

### Post by damis648 on 2008-10-17
> **jerome1232 said:**
> Is ithis a cd-rom your talking about? Like I said the u3 software won't work inside ubuntu, the usb sticks will work as normal though.

+1, mine used to work. (Lost it though... :'()

---

### Post by J03y on 2008-10-17
> **jerome1232 said:**
> Is ithis a cd-rom your talking about? Like I said the u3 software won't work inside ubuntu, the usb sticks will work as normal though.My usb stick doesn't work. When i try to open it it always says, "Unable to mount media. There is probably no media in the drive". :(

---

### Post by jerome1232 on 2008-10-17
ok with it inserted can you post the output of this command

```
sudo fdisk -l
```

---

### Post by J03y on 2008-10-17
> **jerome1232 said:**
> ok with it inserted can you post the output of this command

```
sudo fdisk -l
```Can I run a terminal command while I'm installing the 7.10 upgrades?

---

### Post by jerome1232 on 2008-10-17
yes, i'm going to be out for a bit just fyi.

---

### Post by J03y on 2008-10-17
> **jerome1232 said:**
> ok with it inserted can you post the output of this command

```
sudo fdisk -l
```When i ran the command i got this:  

Disk /dev/hda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7145    57392181   83  Linux
/dev/hda2            7146        7474     2642692+  82  Linux swap / Solaris

---

### Post by jerome1232 on 2008-10-17
With the usb disk plugged in? No drive but your internal is being picked up right there...

this command may show some more info (what's connected to the usb ports)
```
lsusb
```

---

### Post by Keen101 on 2008-10-17
I believe there is a program on the scan disk site that will allow you to disable the U3 option.

I did that to my u3 drive, and it works fine. I had to use the program to reformat it in windows though.

> 3.  	How do I uninstall U3 from my flash drive

Most U3 smart drives come with an uninstall utility that converts the U3 smart drive into a regular USB flash drive. This utility can be accessed from the U3 Launchpad. Open the U3 Launchpad and click on Settings, then select U3 Launchpad Settings and click on the Uninstall tab. Some devices have a link to the Uninstall utility under Help and Support.

If you can not find the uninstall utility on your U3 smart drive you can download it from the following locations:
Remove U3
U3 removal tool for MAC 

---

### Post by jerome1232 on 2008-10-17
That's good info to know I figured it was just a program stuck on a second partition in the usb drive. Apparently it's a bit more complex than that.

---

### Post by J03y on 2008-10-18
> **Keen101 said:**
> I believe there is a program on the scan disk site that will allow you to disable the U3 option.

I did that to my u3 drive, and it works fine. I had to use the program to reformat it in windows though.I downloaded a U3 removal tool but its .exe. I tried to run it with Wine but always says, "Please insert a U3 smart drive", and the U3 is in but it doesn't recognize it. :(

---

### Post by Keen101 on 2008-10-18
> I downloaded a U3 removal tool but its .exe. I tried to run it with Wine but always says, "Please insert a U3 smart drive", and the U3 is in but it doesn't recognize it. 

yeah, you will probably have to borrow a computer with xp or something...

---


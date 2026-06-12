---
title: "How to mount disk raid?"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by paulrollings on 2013-04-17
Hello - many thanks for any advice.

I have a PC with 4 hard disks.  The first disk is a solid state 240GB disk which I boot Ubuntu 12.04 from.  My problem is that I cannot mount or see the other 3 (3TB) disks. 

 I'm a bit confused as I see three bios screens, see enclosed?
[ATTACH=CONFIG]241469[/ATTACH][ATTACH=CONFIG]241468[/ATTACH][ATTACH=CONFIG]241467[/ATTACH]

Becasuse I see the RocketRaid in the last bios screen, I'm assuming that the OS shoudl then see this, so I'm thinking that I just need to work out how to mount this?  I'm googling for an answer, but if anyone has any pointers.

Thanks millions.

Paul

---

### Post by TheFu on 2013-04-17
There are different types of RAID that work under Linux. For home users, using software-RAID is almost always the best choice due to flexibility even with slightly lower performance over true hardware RAID.  Motherboard RAID and cheap RAID cards from most consumer-grade vendors are known as "FakeRAID" for a reason. They require drivers inside the OS for the RAID to work. That's fine for Windows where the drivers are easily available, but less fine for Linux where drivers mean you have to recompile the kernel and relink the drivers - if they even exist - with every new kernel.  If the driver maker doesn't support a PPA or DKMS, it will be a pain to use, in the best case.

I cannot recall seeing any motherboard RAID that wasn't "FakeRAID."  Most people are much better off just disabling the MB RAID feature and using the extremely capable, built-in SoftwareRAID for Linux.  For that to work, you want the JBOD setting - Just a Bunch Of Disks, then use **mdadm** to create, assemble and mount the RAID set.  There are lots of easy to use **mdadm **guides.  

I'll be adding 2 more 2TB disks into a new RAID1 set tomorrow. It will be softwareRAID for many, many, reasons.

Ok, with all that said, you'll need to be extremely specific about the RAID chips used for anyone here to help with drivers and a how-to.

---

### Post by DuckHook on 2013-04-17
> **TheFu said:**
> There are different types of RAID...extremely specific about the RAID chips used for anyone here to help with drivers and a how-to.

++1
Just had to observe how helpful and well-said this post is. I learned something new today. Thanks for sharing.

---

### Post by paulrollings on 2013-04-19
Thanks for the response.  Apologies I am a N00b.   I think my problem why I am not seeing the disks in the OS is because the disks are attached to a HighPoint RocketRAID 640 card.  I tried to install drivers etc to get this to work but am failing miserably.

---

### Post by TheFu on 2013-04-19
A google of "HighPoint RocketRAID 640 ubuntu"
found this [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

Did you try it?  Seems like editing C code will be mandatory to get it working and the steps are fairly complex, change for every install, require medium-level C and build skills.

---

### Post by paulrollings on 2013-04-19
Yes thanks been through that post but failed because my kernel is on 3.5 and those instructions are only upto 3.2.  I tried to modify the code, but failed.   In the end I gave up on the RocketRaid card and I've uplugged the disks from the card and attached directly to the motherboard.  Now when I boot up I see those disks, which I guess then leads me into creating a software RAID.  (I was aiming for the disks to be seen as a single big bucket of storage).

However, I am using this PC as a single-node Hadoop set-up, so haven't quite figured our whether I should RAID the disks or not, but thats a whole new forum discussion ;-) 

Thanks again for your help..... Paul

---

### Post by TheFu on 2013-04-19
We are all "noobs" on something. ;)  I have hardware here that was purchased on a whim ... or after careful research ... that doesn't work properly with my systems too. Hopefully, you can return that card.

I also bought a RAID card that claimed "linux support" and expected the drivers to be perfect.  Turned out the binary drivers were for a 3 yr old kernel and downgrading to that kernel WAS NOT AN OPTION.  There wasn't any source code. Sometimes I've been surprised too.  Plugging in USB devices where the kernel just sees them, and configures for use. A few printers and scanners have worked that way.

What I learned was to only buy hardware that has native support inside the kernel. If I need to download any external drivers, that is a complete failure and I move on to the next hardware choice.  Actually, the RAID card purchase taught me that. Previously, I hadn't been burned getting drivers directly from the vendor, so I didn't know how easy it could be.  I was warped by my Microsoft background - expecting to need to manually install drivers. It doesn't need to be that hard on Linux, if we choose the well-supported-by-kernel hardware.

---


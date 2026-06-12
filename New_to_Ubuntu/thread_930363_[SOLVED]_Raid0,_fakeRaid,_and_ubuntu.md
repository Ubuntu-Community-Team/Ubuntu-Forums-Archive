---
title: "[SOLVED] Raid0, fakeRaid, and ubuntu"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by WhyCantEveryOSBePerfect on 2008-09-25
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Ok.  I have a few questions.
1).  How can I tell whether I have a true hardware RAID or a fakeRAID?  My intuition says I have a fakeRAID because when I boot the ubuntu CD it recognizes two disks.

2).  In the instructions, if I boot to my Ubuntu DVD and then use the dmraid thing, where does that install?  will it install on the freespace of my Ubuntu DVD, or just temporarily exist in my RAM, or will it unceremoniously overwrite something in one of my windows partitions?

Thanks!

I've been trying to get an ubuntu partition on my computer for like 2 weeks now... this is frustrating!

If any of you guys know your hardware, here are some things I have which may help you determine whether I have RAID hardware or 'fakeRAID'
In my device manager I have

Disk Drives
-RAID0

IDE ATA/ATAPI controllers
-ATA CHannel 0
-ATA Channel 1
-Intel(R) ICH8M Ultra ATA Storage Controllers -2850

Storage Controllers
-Intel(R) 82801HEM SATA RAID Controller
-Microsoft iSCSI Initiator
-Silicon Image SiL 3531 SATA Controller

---

### Post by Ocxic on 2008-09-26
You are right you have fakeRAID, I can guarantee that, for true hardware raid you'd have to spend much $$$ for a motherboard a little less for a RAID card. (between $300-$500 for just the card)

The Ubuntu installer(Alternate CD ONLY) lets you setup RAID while partitioning, while it is fakeRAID it is still worth it.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-26
Okay.  fakeRAID it is, I'm pretty sure it is too even if you didn't reply, I went to support for my laptop and the manufacturer said it was a chipset not a processessor that ran my RAID.

So, a few questions.

This procedure has been tested with Ubuntu 7.04 (Feisty Fawn). Your mileage may vary with other versions. 

Install dmraid

GUI
Boot the Ubuntu CD and select Start or Install Ubuntu 

Go to System > Administration > Software Sources and add the universe software repository. 

Go to System > Administration > Synaptic Package Manager and install the dmraid package. 

Go to Applications > Accessories > Terminal and run 

The Above is from [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
When it says "install the dmraid package"  where does that install to?  WIll it install it on the DVD which I burned the Ubuntu iso file to? Or will it unceremoniously dump it somewhere in my pre-existing windows partition?

---

### Post by unutbu on 2008-09-26
When you boot from a LiveCD, the root filesystem is created in RAM. When you install packages, it will be installed in the RAM filesystem. The installation of the package will not write to your hard drive. It's like any other filesystem except that it will be destroyed upon reboot.

---

### Post by OmnyDevi on 2008-12-31
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I got it all good up until configuring grub came into play. Cannot get grub to work on fakeraid0 for anything. :/

---

### Post by loopzilla on 2009-10-28
> **OmnyDevi said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I got it all good up until configuring grub came into play. Cannot get grub to work on fakeraid0 for anything. :/

I have a similar problem !
Grub fails with error 17 :(
What did you do to solve this problem ?
I suppose that problem is that the grub can't see raid0 disk arrays.
How can he load his config (I mean /boot/grub/menu.lst) ?

---

### Post by sux2bu101 on 2009-11-06
I am looking for a solution to this problem also.

---


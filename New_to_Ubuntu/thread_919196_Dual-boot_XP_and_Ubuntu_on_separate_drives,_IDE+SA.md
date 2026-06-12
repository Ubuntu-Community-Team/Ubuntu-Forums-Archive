---
title: "Dual-boot: XP and Ubuntu on separate drives, IDE+SATA, no boot loader"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Trubadurix on 2008-09-13
Hi!

since I'm posting in the absolute beginner talk section, it's fairly obvious I'm an absolute beginner. Trying to install ubuntu for the first time tonight.

My machine has three harddrives with the following partitions
[LIST=1]
[*] 750 GB SATA
[LIST]
[*] C: NTFS, approx 100GB (Windows drive)
[*] D: NTFS, remaining space (containing various junk)
[/LIST]
[*] 200 GB P-ATA ("IDE")
[LIST]
[*] F: NTFS, 200 GB (empty)
[/LIST]
[*] 200 GB P-ATA ("IDE")
[LIST]
[*] Swap: 4096MB (RAMx2)
[*] Root: Ext3, 10GB
[*] Home: Ext3, remaining space
[/LIST]
[/LIST]

I wanted to try Ubuntu without messing around with the Windows drive, so I installed it to a separate (physical) drive.

During the installation of Ubuntu, I did *not* unplug the windows drive. I was going to, but asked on IRC first, and was told not to if I wanted things to work without trouble. (hah)

Anyway, I installed Ubuntu according to the documentation, to the best of my ability. **The problem I have now is that upon starting the machine, I have no option which OS to load. It loads Windows XP without asking.**

In the BIOS, there is a "boot device priority" list:
[LIST=1]
[*] [IDE:TSSTcorp CDDVD]
[*] [SATA:SM-SAMSUNG HD]
[*] [ATAPI CD-ROM]
[*] [Disabled]
[/LIST]

Which drive shows up in spot nr 2 is decided by my selection in another list of "hard disk drives"
If I change the 1st drive to the IDE drive containing Ubuntu, it will load without any trouble (apart from being very slow)

I should probably also note that during the installation, the SATA drive did not show up on the overview screen where one prepares partitions prior to installing.

Here's a snippet I wrote down during installation. Not sure if it's meaningful, but I was puzzled that it begins with partition #5 on an empty disk:
> the following partitions are going to be formatted:
partition #5 on SCSI1 (0,0,0) (sda) as swap
partition #6 on SCSI1 (0,0,0) (sda) as ext3
partition #7 on SCSI1 (0,0,0) (sda) as ext3

I will be using windows as main OS for now, but would like to have the option of choosing Ubuntu without first having to change boot priority.

Any help is very much appreciated. I've tried to include all the info I have, but if I need to provide any more info, please just ask (and preferably tell me how to acquire it).
As I said, I can access both Windows and Ubuntu, I just don't have a boot option.

*(ps! I've come down with the flu during the day, and will be crashing very soon. I'll look at this thread again in about 8-9 hours)*
:frown:
Thank you!

---

### Post by louieb on 2008-09-13
IDE + SATA drives on the same computer often leads to GRUB install confusion. The installer tries to get the boot order from BIOS but sometimes it gets it wrong.

It can be done but your going to have to do some manual configuration of GRUB. Take a look at this thread it should help you get dual boot working.  
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by rraj.be on 2008-09-13
> **Trubadurix said:**
> Hi!


[*] Swap: 4096MB (RAMx2)
[*] Root: Ext3, 10GB
[*] Home: Ext3, remaining space

Having 2X Ram As swap is prefered untill your swap was < 2 GiB.

But if your swap is above 2 GiB it was a waste.

2 GiB of swap is more than enough.

> 
During the installation of Ubuntu, I did *not* unplug the windows drive. I was going to, but asked on IRC first, and was told not to if I wanted things to work without trouble. (hah)



You should add your OS to GRUB.
Its preferable tto connect all your hard disks while installing so that it
automatically lists all hard disks and all OS in it so that it could be added to your GRUB [Boot loader]

Now to add your Windows to GRUB follow the steps

1) Boot into Live cd [Ubuntu]

2) Open terminal.

3)Type ```
sudo grub

find /boot/grub/stage1
```

If it returns like ```
[hdaX,Y]

```
type

```
root[hdaX,Y]

setup [hdaX]
quit

sudo reboot
```

---


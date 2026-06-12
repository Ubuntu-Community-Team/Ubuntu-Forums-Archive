---
title: "Oneiric 11.10 beta2: impossible to partition disk"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quaxo76 on 2011-09-25
I'm trying to install Oneiric beta2 on a spare partition on my laptop. My disk has complex partitioning, with 12 separate partitions and some free space. On sda12 there is an old system that I wish to replace with Oneiric.

I downloaded the 11.10 iso, and set up a live-usb with unetbootin. The livecd boots fine and is usable. When I proceed with the installation, it gets to the point where you set up the partitioning; instead of "use the whole disk" I choose "manual", but the next screen doesn't show the available partitions. The only option is to format/repartition the whole drive.

If I run GParted, it shows the whole disc as "not allocated".
But if I run Disk Utility, I can see all the partitions without problems. And of course, if I boot the other systems in the other partitions, they work, so I know that the partitions are actually there.

Known bug? Is there a workaround?

Thanks,
Cristian

---

### Post by Stephan Volkmann on 2011-09-26
> **Quaxo76 said:**
> I'm trying to install Oneiric beta2 on a spare partition on my laptop. My disk has complex partitioning, with 12 separate partitions and some free space. On sda12 there is an old system that I wish to replace with Oneiric.

I downloaded the 11.10 iso, and set up a live-usb with unetbootin. The livecd boots fine and is usable. When I proceed with the installation, it gets to the point where you set up the partitioning; instead of "use the whole disk" I choose "manual", but the next screen doesn't show the available partitions. The only option is to format/repartition the whole drive.

If I run GParted, it shows the whole disc as "not allocated".
But if I run Disk Utility, I can see all the partitions without problems. And of course, if I boot the other systems in the other partitions, they work, so I know that the partitions are actually there.

Known bug? Is there a workaround?

Thanks,
Cristian

you can try to boot from your stick with option "No dmraid", that is on F6 or so.. in bootscreen on the bottom

---

### Post by oldfred on 2011-09-26
Do you have a NTFS partition? If so try chkdsk.

I thought the newer gparted was a bit better, but a couple of versions ago gparted would not show my sda drive which was XP. I could boot XP but it was somewhat slow. After I ran chkdsk on my NTFS partition gparted would show sda, XP booted somewhat faster and so did Ubuntu (related to mount of NTFS partition??).

---

### Post by tekstr1der on 2011-09-26
> **oldfred said:**
> Do you have a NTFS partition? If so try chkdsk.

I thought the newer gparted was a bit better, but a couple of versions ago gparted would not show my sda drive which was XP. I could boot XP but it was somewhat slow. After I ran chkdsk on my NTFS partition gparted would show sda, XP booted somewhat faster and so did Ubuntu (related to mount of NTFS partition??).

The latest gparted 0.9.1-1 Stable (released last week) uses up-to-date ntfs libraries again. Previously there were some issues which caused a few recent builds of gparted to use older libraries temporarily.

> 
This release resolves a problem with resizing NTFS file systems that is described in Bug 655215 - NTFS partition resize fails. Packages ntfs-3g and libntfs3g were downgraded to 2011.1.15AR.4-2 to resolve this problem for the near term. This release is based on the Debian Sid repository as of July 28, 2011 (linux kernel 2.6.39-2).

---

### Post by Quackers on 2011-09-26
Quaxo76, are your partition problems from your previous threads now fixed?
It seems not.

---

### Post by crencom on 2011-09-26
I am having the exact same issue.  Windows 7 installed on the partition.  It basically does not recognize the W7 installation and the on ly option is to format the entire drive.

---

### Post by oldfred on 2011-09-26
@crencom
Welcome to the forums, but with Windows 7 your problem is probably different. Please start a new thread and post this from liveCD or screenshots from gparted or Windows to see partition layout.
sudo fdisk -lu

---

### Post by dino99 on 2011-09-26
> **oldfred said:**
> Do you have a NTFS partition? If so try chkdsk.

I thought the newer gparted was a bit better

Sadly the latest stable gparted is still not packaged: 
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213)

and worst: it is set as whishlist

---


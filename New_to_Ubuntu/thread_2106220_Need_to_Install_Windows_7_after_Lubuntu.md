---
title: "Need to Install Windows 7 after Lubuntu"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by AlphaQ on 2013-01-18
Now I installed Lubuntu on my desktop after overwriting Win7.
My Dad isn't particularly comfortable with Lubuntu and wants Win7 back. Now I thought of Dualbooting Win7 along with Lubuntu but I cant partition the drive while installing Windows 7. Please help.

---

### Post by MoebusNet on 2013-01-18
Everything I've ever read about dual-boot said the same thing; Ubuntu needs to be installed *after* Windows. This is a requirement of Windows, not of Ubuntu.

This will give you a more complete idea of what is going on:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I recommend you **back up** all of your Dad's data before you start the installation(s).

---

### Post by GordThompson on 2013-01-18
The first thing to check is whether you have

1. a "normal" Windows installer disk, or

2. a "System Recovery" disk, as is often supplied with machines where Windows is pre-installed.

---

### Post by GordThompson on 2013-01-18
> **MoebusNet said:**
> I recommend you **back up** all of your Dad's data before you start the installation(s).
According to one of the OP's [earlier threads]("http://ubuntuforums.org/showthread.php?t=2091884") it may be too late for that....

---

### Post by oldfred on 2013-01-18
Windows prefers to be first but can be installed to any primary (sda1 thru sda4) partition formatted NTFS with the boot flag. Or to unallocated space with available primary partitions.

Windows 7 will normally install to two partitions, a small hidden 100MB system or boot/repair partition and the main install. But it will install to one partition.

Edit:
Above info is only for a full Windows install. If a recovery set of DVDs then that normally is just an image of hard drive as purchased and will just restore system to the day you purchased it, erasing everything. Always better to have full backup of Windows and use that to restore.

---

### Post by leclerc65 on 2013-01-18
I have never done this, but have a plan for you

1- Use Gparted (live CD or within Parted-Magic CD), shrink your Ubuntu partition then make a NTFS partition for Windows.
2- Install Windows
3- Repair boot by the following steps
   a- boot with an Ubuntu live CD, option 'Try Ubuntu'
   b- Open a terminal then do
      sudo mount /dev/sdaX /mnt 
      (replace X with the number of the partition where Ubuntu is installed, also assuming your hard drive is SDA) 
      sudo grub-install --root-directory=/mnt/ /dev/sda
   c- reboot, you shoud have Ubuntu by now
      sudo update-grub
      reboot , you should see options to boot Ubuntu & Windows

I'd rather backup the data, and start from scratch. Shrinking partions is slow and sometimes dangerous.

---


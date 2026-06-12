---
title: "Problem installing Ubuntu 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mzbeg on 2008-04-25
Hi all

I installed 8.04 from Window XP rebooted into Ubuntu using the Verbose mode and got the following messages :

ata3.01=status {DRDY}
failed to read native max address (err-mask=0x4)
failed to reconnect some devices
revalidation failed (err0-5)

And many more.

The problem in Verbose mode is Pause/Break key does not work in order to write down all the messages.

I have Samsung 500GB partitioned as follows:

C:\Windows XP Primary 
D:\Ubuntu; E:\ F:\ G:\ H:\ and all logical partitions.

I tried Safe Graphic Mode and got 3.01=status {DRDY}
ACPI workaround ata3.00=status {DRDY}

I do not know what it all means. Can any one help me please. Thanks.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - SATA Samsung SH-S203LJ DVD RW - ATA POINEER DVD-RW DVR-109 - EZCOOL Case - WINDOWS XP Service Pack 3.

---

### Post by adieb on 2008-10-07
Hello,

that means that there is a problem with your ATA-Controller. Ubuntu (or better the Linux-Kernel) can not read hardware information corectly.

Actually I don´t know about the Installation from Windows. But I can imagine, that that caused a problem.

In Linux you don´t have C:, D:, E: and so on.
It arranges all devices in [controller][disk]
So for example disk 1 on ATA controller: hda
disk 2 on ATA controller: hdb
disk 1 on SATA/scsi controller: sda

Numbers behind these descibe a partition on that specific disk.

Ok, all this is surely no solution for you. Because your post is older, i think you already found a way. New relase for example.

For all other who have these problems now, you try to install through live disk.

---


---
title: "The booting process"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by davidc60 on 2011-12-01
Hi, 
I have recently been attempting to install a Linux distro on to a bootable memory disk. At the stage of the process when the relevant partitions are determined the installation wizard proposed the following set-up:
dev/sdc
dev/sdc1 1mb BIOS Boot
dev/sdc2 500mb /boot
dev/sdc3 5062 / (ie.root)
dev/sdc4 2015 swap
My first question is about the term "BIOS Boot" - is that exactly the same as the 'Master Boot Record' or are they two entirely different things? 
Secondly,(assuming BIOS Boot and MBR are one and the same) what would be the effect/significance **in practical terms **of the BIOS Boot/MBR being on dev/sdc1 rather than on dev/sdc.
Thanks,
davidc

---

### Post by carverj on 2011-12-01
So the BIOS is the read-only firmware software that is the first software run when you turn on the computer. It will initialize hardware connected to the machine including the hard drive which contains a MBR at the beginning or first sector. The MBR when executed, knows the partition table information for that hard drive and assists with execution of the bootloader program.
So BIOS and the MBR are two separate components that team up during the boot process.

---

### Post by mcduck on 2011-12-01
> **davidc60 said:**
> Hi, 
I have recently been attempting to install a Linux distro on to a bootable memory disk. At the stage of the process when the relevant partitions are determined the installation wizard proposed the following set-up:
dev/sdc
dev/sdc1 1mb BIOS Boot
dev/sdc2 500mb /boot
dev/sdc3 5062 / (ie.root)
dev/sdc4 2015 swap
My first question is about the term "BIOS Boot" - is that exactly the same as the 'Master Boot Record' or are they two entirely different things? 
Secondly,(assuming BIOS Boot and MBR are one and the same) what would be the effect/significance **in practical terms **of the BIOS Boot/MBR being on dev/sdc1 rather than on dev/sdc.
Thanks,
davidc
No, it's not the same as MBR. Since the installer is suggesting such partition I'd assume you have a recently new system that's using UEFI instead of BIOS.

edit: Come to think of it, since it's named as "BIOS partition" it's more likely that your computer still uses BIOS, but the disc is partitoned using GPT instead of the older MBR scheme. Either way, you should leave the partiton as it is, it's not the same thing as MBR (or even the same thing as /boot partition) and you'll pretty much need it for the system to work.

By the way, is there a specific reason for creatin gthe /boot partition? In most cases that's only going to cause you troubles... Unless you are either using a computer so old it's not able to boot froma s large hard drive as you have, or you are using some type of RAID setup, I'd recommend against the separate /boot partition.

[http://en.wikipedia.org/wiki/EFI_System_partition]("http://en.wikipedia.org/wiki/EFI_System_partition")
[http://en.wikipedia.org/wiki/BIOS_Boot_partition]("http://en.wikipedia.org/wiki/BIOS_Boot_partition")

(MBR is *never* on a partition it's by definition the first sectors of a disc so it always comes bbefore any partitions. And on the other hand UEFI pretty much *requires* a partition of it's own.

---

### Post by oldfred on 2011-12-01
I installed Ubuntu in a 16GB flash drive and I did use gpt just to learn about gpt. Is not the first partition bios_grub? That is where grub has to put core.img as in gpt there is no space after the protective MBR. gpt only has a MBR so older software knows it is different.

Since I installed to flash and have 4GB of memory I did not create swap at all.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

If using gpt create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

---

### Post by davidc60 on 2011-12-02
Hi,
Thanks to everyone for theirhelpful replies on this thread.
davidc

---


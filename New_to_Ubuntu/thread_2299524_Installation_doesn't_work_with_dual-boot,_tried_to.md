---
title: "Installation doesn't work with dual-boot, tried to partition like in a video..."
date: 2015-10-19
forum: New to Ubuntu
---

### Post by passt on 2015-10-19
Hello World,

I don't know in which forum this should be, because i have got installation problems with my hardware ( i think so ). I wanted to install Ubuntu 15.04, and it was all working until i had to select boot partitions etc.
I've got preinstalled Windows 10 on my Laptop and 1 SSD (256 GB) + 1 HDD (1 TB). I tried to partition the SSD, where a few things are (Sorry for my bad english, it's not my mother-language).
Here's a quick overview of my partitions:
-sda:
partition..............          |        file system...........          |         flags
-----------------------------------------------------------------------------------
sda 1.................             |          fat 32                ...................| boot, esp
-----------------------------------------------------------------------------------
sda2...................              |      unknown..............               | msftres
-----------------------------------------------------------------------------------
sda3              ..................|            ntfs......................                | msftdata
-----------------------------------------------------------------------------------
unallocated     ........|.............................                                 |                          
-----------------------------------------------------------------------------------
sda4              .................|            ntfs........................                | hidden, diag

-sdb:

partition............        |    file system    .|...   flags                
-------------------------------------------------------------------
sdb1................            | ext4............                 | msftdata
-------------------------------------------------------------------
unallocated  .......|....................                         |                  

I can't choose the option "Extended Partition" in the menu of GParted, when i click on "New" on "unallocated". So, i don't know why, and actually, i installed Ubuntu but i don't know where and i can't also boot with Ubuntu, there is no boot menu where i can choose Ubuntu or WIndows. I need Windows for school (PowerPoint etc.).

Can anyone help me with my problems?

Thanks for all helpful answers.

---

### Post by james_moore2 on 2015-10-19
I would just launch the installer, there should be an option that looks like this "Install along side Windows 10" or something like that. Please provide any pictures if you can.

---

### Post by grahammechanical on 2015-10-19
Gparted is a powerful tool and it has be useful for those of us who have a BIOS boot system and an msdos partitioning scheme as well as those who have a UEFI boot system with a GPT partitioning scheme.

You have Windows 10 pre-installed therefore you have a UEFI boot system and GPT partition scheme. Extended and Logical partitions are only relevant to motherboards with the BIOS boot system and msdos partitioning scheme. That is why Gparted will not let you create an Extended partition.

Gparted will let you create a primary partition in any unallocated space. Actually, you will need 2 partitions for Ubuntu. One for Ubuntu itself and one for swap. And then when you run the installer you will need to select the Something Else option and direct the installer which partitions to use.

As already suggested you could, after creating sufficient unallocated space, choose the Install Alongside option. But please read this wiki page and note the heading: The case when Ubuntu must be Installed in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 10 will most definitely be installed in EFI mode.

Regards.

---

### Post by passt on 2015-11-16
> **james_moore2 said:**
> Install along side Windows 10
There is an option that means "Install along side Windows Vista... I wondered why there is Windows Vista and not Windows 10. I'll try it again until it works.

---

### Post by yancek on 2015-11-16
I've never seen an option that specifies a version of windows like vista so that seems a little weird but I doubt that has anything to do with your problem.  You might have better luck and certainly will have more control over the installation if you select "Something Else" from that menu.   You need to make sure you are using the EFI install method rather than MBR and that should be available when you boot the installation medium.  The output in your initial post shows that windows has an EFI partition so Ubuntu must also be installed using EFI.

It would also be more useful if you posted the actual image from GParted.

---

### Post by sandyd on 2015-11-16
> **passt said:**
> There is an option that means "Install along side Windows Vista... I wondered why there is Windows Vista and not Windows 10. I'll try it again until it works.

Do **not** partition it in Ubuntu, or Gparted for that fact.

Some people have experienced boot issues or disk checks after resizing the Windows partition in Ubuntu, and had have to do a disk check.

Instead, boot Windows, go to Control Panel -> Administrative Tools -> Computer Management -> Disk Management.

Create free space there, and then you can use the free space in Gparted.

Please make sure you disable fast start in Windows if you want to access Windows partitions from Ubuntu.

---

### Post by passt on 2015-11-30
I really don't know what i should format and with what, and so on.
Ubuntu won't start with grub, Windows starts and nothing with Ubuntu happens.
But if i format the Ubuntu partitions, there is an OS.
Maybe, it must be in the Windows partition, for grub autostart and not Windows autostart.
I'm thinking about a tinier Laptop, only for max. 100 € ( i know he cannot be good ), for installing Ubuntu and programming and this stuff. And my Asus Laptop now for playing computer games.
Can you give me advise?

---

### Post by sandyd on 2015-11-30
The issue is that you have no bootloader in /dev/sda.

What you have to decide now is if you want to use the full SSD for Windows, and then part of the 1TB for Linux, or something else.

We can guide you along to help you do your setup if you tell us the configuration you want.

---


---
title: "How to install Ubuntu ? [UEFI Problem]"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by GakuWai on 2015-04-04
Hi,
So I have a latest Ubuntu on my disc but I can't install it because I have that stupid new standard called UEFI which by thanks to it GRUB can't be installed :mad::mad::mad:.
I want to install Ubuntu with encryption so I usually create /boot and then rest of the partitions which I select to encrypt and that was working on all my old computers before that UEFI thing but now when I try to do it, my Ubuntu installation can't install GRUB and I stuck, I heard that I need to create two partitions bios_grub, biosgrub but while I was partitioning I couldn't it ? :-|

Any ideas ? 
Every help is appreciated.
Thank You.

---

### Post by grahammechanical on 2015-04-04
The problems might not be to do with UEFI. Well, not exactly, anyway. But we cannot tell as you do not describe in detail the problem. What happened? Did you install using the Something Else option? Is there Windows 8 on this machine. Did you follow the recommendations in this Wiki page?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you run Boot Repair. That will produce a summary report and provide a URL to a Pastebin page where the report is stored. Paste that link in this thread then we can see the report. You can do that before accepting Boot Repair's recommended repair if you want. By the way, Boot Repair puts it recommendation at the bottom of its report.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by oldfred on 2015-04-04
You need either an efi partition or a bios_grub partition if using gpt partitioning.
You can use the old MBR(msdos) partitioning but then can only boot in BIOS mode.

I suggest both efi at beginning of drive and a bios_grub partition. Then you can later change without major issues as efi should be first. The bios_grub can be anywhere on drive.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

How you boot install flash drive is how it installs. Or if you boot in UEFI mode it installs in UEFI mode.
I do not use nor know much about LVM & full drive encryption, but some have posted the Summary report from default installs and they have the efi partition, a boot partition and a partition where the LVM is installed inside for / & swap.

I suggest about 300MB for an efi partition formatted FAT32 with boot flag, 1 or 2MB for a bios_grub partition unformatted with bios_grub flag. You then need your /boot whatever size you like as ext2 or 4. Default installs seem to use ext2 as it is small and journal with ext4 does not add much.  Many with default installs have had about 250MB, but never housecleaned kernels and had issues with /boot getting full.

To get gpt partitioning if partitioning in advance with gparted. 
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

And gparted cannot create LVM partitions, just standard partitions.

---

### Post by GakuWai on 2015-04-04
OK, thanks guys and gals for suggestions, I will try to do what you have told me to and will come back soon with results.

---


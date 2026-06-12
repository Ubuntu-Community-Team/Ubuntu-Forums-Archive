---
title: "Ubuntu 12.04 insstallation doesnt  detects windows 7"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Lancro on 2012-04-28
Hi, I want to dual boot, but the installer only give me the options of deleting the entire disk or advanced, and it tolds me no other operative system has been found, I have multiple partitions in this computer, recovery and that all stuff, any idea how could the installer find my windows 7 installation so I can install ubuntu alongside windows 7?.

Thanks.

---

### Post by Lancro on 2012-04-28
More data I have 4 partitions...

1.- EFI System partition 300 MB
2.- A partition called DELLUTILITY with 40MB fat32
3.- A partition called OS with Windows 7 and data file (This is where ubuntu should detect windows 7 and installs)
4.- A partition called RECOVERY with 750 MB

I hope this helps, thanks.

---

### Post by oldfred on 2012-04-28
A few vendors just labeled their vendor partition efi, but generally a efi partition should be the efi partition and you boot via UEFI.

From your UEFI screen you should load the Ubuntu liveCD or USB so you are in UEFI mode. 

Another user posted this:
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
You may want to partition in advance and definitely backup your efi partition. There was (is?) a bug in grub that it overwrote the efi partition and erased the Windows efi boot files.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

Useful info even if not Ubuntu:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---


---
title: "EFI partition failing"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by ggxdg on 2012-07-09
I've been trying to install ubuntu for a few days now, stubborn as I am.
I've been looking everywhere for an answer.

First I installed ubuntu with a normal /boot partition with a size of 500MB, no errors, but it skips the SSD ubuntu is installed to, and right on to the raptor-drive windows 7 is installed to.
For now I don't care about dualboot, I just want to get grub installed and I want it to react.

After reading around different forums, I found that I might need an EFI partition. Now trying an EFI boot partition instead of the boot partition, results in:

"The attempt to mount a file system with type vfat in SCSI2 (0,0,0), partition #1 (sda) at /boot/efi failed

You may resume partitioning from the partitioning menu."

I have yet to come across some list of how to set up the partitions. I've foud rather specific setups, but nothing on how to set up EFI-boot
For some reason, I can't find my SSD or my Raptor in the HDD list when choosing "Install along side Windows 7".

---

### Post by oldfred on 2012-07-09
With multiple drives and systems, it is better to partition in advance with gparted. Also just about everyone with UEFI has posted that they had problems, but by partitioning in advance then it just worked.

How is Windows installed? Is it UEFI/gpt or BIOS/MBR. With the new UEFI systems, both Windows and Ubuntu should show both UEFI and legacy/BIOS/AHCI/oldway however the call it. Some new UEFI also have a way to turn on/off the UEFI boot.

Best to install Ubuntu in the same way Windows is installed, or both should be UEFI or both should be UEFI.

If installing only Ubuntu on a drive you can use gpt partitioning whether UEFI or BIOS. But Windows will only boot from gpt drives in UEFI.

An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

One suggestion on partitions:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by ggxdg on 2012-07-09
Ah... This is fantastic knowledge, exactly what I've been looking for! Thanks a bunch!

If this is a frequent problem, might I suggest a sticky? Unless of course it clutters up the first page.

I did see others talking about using gparted, but I'm stubborn, so I kept using the installation partition tool. But I guess if it's the only way, I'll have to stop being stubborn :P

I'm certain that Windows is installed the "old way" (BIOS/MBR) as you so aptly described it :)
Oh well, I guess it's time to format the windows-drive then.

I can disable UEFI-Boot, but I'd greatly prefer to have everything working with the new tech.

---

### Post by ggxdg on 2012-07-09
Ah... should have written a few more details at first, then I bet you would have found the exact problem straight away.
I had the EFI-partition set to 500MB. Just to figure out exactly what I did wrong, I tried everything as I had it, only, I changed the EFI-partition from 500 to 200MB, and now it works like a charm.
However, before I get to comfy here in ubuntu, I'm going to follow some of your advices.

Again, thanks a bunch - this was pure gold!

---

### Post by ggxdg on 2012-07-10
I have to say, I'm a little surpriced that the Ubuntu installer partitioning tool, allows for EFI-boot-partition above 256MB, if EFI (boot record?) ends at EF00. Is it to make sure that it might work with future EFI upgrades/updates?

---

### Post by oldfred on 2012-07-10
The ef00 is just the code in the partition table to tell that it is the "boot" partition.

I think the limits of the efi partition are more related to the limits of the FAT32 driver that they built into the efi boot loader. One user did not have it first and it still worked but I think the limits of the driver is why they want it first so there will be fewer issues. It does not need to be a large partition, but if dual booting you may need room for two efi boot loaders as everyone is using the same efi partition.

---

### Post by ggxdg on 2012-07-11
Yeah, in some of the guides I've read, they also said that it didn't necessarily have to be the first partition. However, none of what I had read, said anything about the maximum size of the partition, which I had gone way over.
It still surprises me a little, that if nothing works with an EFI-partition above 256MB, that the installer doesn't have a limit on the size of that particular partition.

Ubuntu is purring like a kitten now... Extremely fast (faster in general than windows 7, but I guess the SSD doesn't hurt :P) and just as pleasant as I remembered it to be. I can't seem to install en EFI-version of windows though. Formatted the drive, converted it to GPT n' all, but when running windows EFI installer, it stops because it can't connect "to the device" error code 0xc000185. Apparently I'm the only person on the internet that have have that error on that installer. But I'll go bother some windows forums on that issue, after I try downloading an image, and chuck it on a USB-key and try installing from there.
Also my ASUS EFI boot-loader thingymagig (can't remember the exact name, but some people uses it to mess about n' getting stuff to react), also can't load, so it's likely I need to try n' flash it.

---


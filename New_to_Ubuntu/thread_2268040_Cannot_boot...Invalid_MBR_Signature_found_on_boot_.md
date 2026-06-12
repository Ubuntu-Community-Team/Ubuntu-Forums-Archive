---
title: "Cannot boot...Invalid MBR Signature found on boot partition"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by wilderf353 on 2015-03-05
I am not sure how to fix this. I have tried using the boot-repair-disk, but no luck.

I did post a Boot Info Script at [http://paste.ubuntu.com/10542487/](http://paste.ubuntu.com/10542487/)

Any chance of someone helping me?

Thanks

---

### Post by oldfred on 2015-03-05
Did you run Boot-Repair and accept the fix suggested. It says you did not with the Summary posted.

Grub issues are often related to different versions of grub in MBR and in install.

Once you get it working, you may want to houseclean some older kernels.

---

### Post by m-j-feeney on 2015-03-05
I had turned off the secure boot, using the boot-repair. this did the trick for me.

---

### Post by wilderf353 on 2015-03-06
I performed another grub repair using Boot-Repair, now I am getting an "error: attempt to read or write outside of disk 'hd0'" and then I get a kernel panic and the computer needs a hard restart.

I posted a new BootInfo summary at [http://paste.ubuntu.com/10551042/](http://paste.ubuntu.com/10551042/)

Any idea of why my machine is attempting to read outside of disk hd0?

Thanks

---

### Post by oldfred on 2015-03-06
Is this an older computer (older BIOS) with new 3TB drives?
Some very old BIOS would not boot from beyond the first 137GB of a drive. So either all of / (root) or a separate /boot had to be fully inside the first 137GB of the drive. But that was very old BIOS, and most newer should not have that issue.

Also sdb is not partitioned. Grub does scan system with the search by UUID function. Not sure if then not being able to scan sdb is causing an issue. I might at least partition that drive.

With multiple drives do not run auto fix in Boot-Repair. It just installs grub to the MBR of every drive. generally you only want grub installed to the MBR of the same drive as your install and you may (should) have installs on all large drives just as a backup way to boot with its boot loader on that drive. You can use advanced mode in Boot-Repair or manually install grub. Sometimes if major errors the full uninstall/reinstall of grub is required.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by wilderf353 on 2015-03-06
No, it is a new computer that I built last fall (Gigabyte 990FXA-UD3 with 16G). 

Yes, sdb is not partitioned. I just added it a few weeks ago. I am trying to set up RAID.

It has been working fine. I install some updates over the last week or so. When I did a reboot a few days ago, this problem started. I need to check if there was a new update for grub that might of broken something on Gigabyte MB.

---

### Post by oldfred on 2015-03-06
It seems all newer Gigabyte boards need IOMMU setting in UEFI.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by wilderf353 on 2015-03-11
Thanks for everyone's help.

I tried some of the things that oldfred suggested and a few other things I found searching the net.  I finally got it working by booting to an earlier version of the kernel and reinstalling the last version that was giving me trouble. It now boots, just like it used to. Note: I made other changes before re-installing the kernel...those change may or may not have been needed (like [COLOR=#000000]set ACPI=Off and nomodeset,)[/COLOR].  

Thanks again

---


---
title: "Dual Boot issues with Win 10 and Ubuntu 19.04"
date: 2019-04-26
forum: New to Ubuntu
---

### Post by whalanboy on 2019-04-26
I have recently installed Ubuntu 19.04 on my system that already had Win 10 installed. 

The system has:
1tb drive for Windows currently partitioned 524mb System partition 999gb NTFS filesystem (this is where win 10 resides) and  a 496mb NTFS partition that i cannot access that was setup by win 10 installation
2tb drive for general file storage that is formatted NTFS
Not wanting to mess up what I already had I have used a separate 2tb HDD for  Ubuntu that was partitioned 100mb/Boot 1gb/swap and the remainder of  2tb/EXT4.

At first grub screen was not showing at all so i used Boot repair and this has the menu show but the menu does not show the windows installation. I re-ran boot repair to try again and get an error message to create a boot partition but I already have one.
I have run boot repair for a Boot info summary the results are available here: [http://paste.ubuntu.com/p/tVTyWz6TqC/](http://paste.ubuntu.com/p/tVTyWz6TqC/)

 Any help to get my windows to be available again would be greatly appreciated.

---

### Post by yancek on 2019-04-26
The link below is the official Ubuntu documentation on dual booting with windows 10 and Ubuntu in UEFI mode.  Your windows system is not UEFI which is unusual but your Ubuntu install is.  If you read the link below, it explains why this is a problem.  THe two don't mix well and the message you are getting about a boot partition is for a GPT/Legacy system.  You don't have a boot partition, you have an EFI partition (sdc1) which contains some boot files while the rest of the boot files are on sdc3 which is the system partition for the Ubuntu OS.

You might try the advice at the bottom of boot repair to activate or mark as bootable the EFI partition (sdc1) which you can do from GParted.  GParted is on the Ubuntu install medium so run that and go to the Partition tab at the top and down to Manage Flags and make sure the boot and esp boxes are checked.  Run sudo update-grub after and see if you get a windows entry.  IF that doesn't work, you may need to convert Ubuntu into Legacy mode.  All this is explained at the link below. 

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-04-26
While it would be better to re-install Windows in UEFI boot mode since you have UEFI hardware, you can get it working again quickly by installing a Windows boot loader to MBR of sda. Boot-Repair may install the syslinux boot loader using advanced mode and choose operating system & drive sda.
If not you have to use Windows repair disk and fixMBR command.

Do not run autofix in Boot-Repair with multiple drives. It installs grub into MBR of all drives if in BIOS mode. Since you have a Windows only drive, you want to keep Windows boot loader in MBR of Windows drive.

Since separate drives, you can boot Windows in BIOS mode & Ubuntu in UEFI mode, but not from grub, only from UEFI boot menu. You may need to turn on/off UEFI settings, but most systems will auto switchs to match system you boot. Grub will only  boot other systems in same boot mode.

You can also convert Ubuntu to BIOS boot on gpt drive. Boot-Repair latest report shows it.
You have to add a tiny 1 or 2MB unformatted partition with the bios_grub flag for grub to correctly install in BIOS boot mode. Then run Boot-Repair to reinstall grub, but only to Ubuntu drive, not to sda, the Windows drive.

Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in the 35 year old MBR partitioning with BIOS.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by whalanboy on 2019-04-27
Thank you for your help. While the issue hasn't been resolved your assistance has pointed me at the cause of my issue. The drive windows is on is too old for the EFI system and as such is not compatible with dual booting unless i reinstall Ubuntu in bios mode or replace the drive that Windows resides on. Given my pc is due for an upgrade I will wait and redo all drives with the upgrade until then bios boot override allows me to choose the OS i want to boot so happy days.

---

### Post by oldfred on 2019-04-27
Its not really the drive. Microsoft has required UEFI/gpt since 2012 & release of Windows 8. So all hardware since then normally supports UEFI.

Windows only installs to MBR partitioned drives with BIOS boot mode.
Windows only installs to gpt partitioned drives with UEFI boot mode.

So it is not particularly easy to convert as you have to redo partitioning on drive. Or you must have good backups of your data.

---


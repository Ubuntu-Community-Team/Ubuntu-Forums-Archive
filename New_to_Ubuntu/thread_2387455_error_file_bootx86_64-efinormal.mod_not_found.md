---
title: "error: file /boot/x86_64-efi/normal.mod not found"
date: 2018-03-19
forum: New to Ubuntu
---

### Post by nekoalosama on 2018-03-19
I am a very new to both Ubuntu and the forums.

I have tried to install Linux, but after installing, the GRUB didn't load. I saw an article online that said I had to change the bootmgr in Windows.

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

After doing that, I restarted my computer. But, unfortunately, it shows the error shown in the title.
I have tried to use boot-repair, but I couldn't because I needed to have a live session in UEFI mode. But the only way for my computer to boot from my live USB is from legacy mode.

I do not know if the problem is because of my hardware or if I had a corruped .iso file.

---

### Post by yancek on 2018-03-19
Did you install Ubuntu UEFI?
Which windows, 8 or 10?

Boot the Ubuntu install usb and select the Try Ubuntu option.  When you get to a Desktop, open a terminal and run this command and post the output here:

```
sudo parted -l
``` THat's a lower case Letter L in the command.  This should tell if you have a UEFI system which is likely.  You can look at the Ubuntu site below to see if you installed Ubuntu UEFI.  If you see a partition named EFI, try navigating there to see if you have an Ubuntu folder.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by nekoalosama on 2018-03-21
Here's the output:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZEX-60W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   934GB   934GB   ntfs            Basic data partition          msftdata
 6      934GB   954GB   20.0GB  ext4
 7      954GB   979GB   25.0GB  ext4
 8      979GB   987GB   7430MB  linux-swap(v1)
 4      987GB   988GB   1028MB  ntfs            Basic data partition          hidden, diag
 5      988GB   1000GB  12.6GB  ntfs            Basic data partition          hidden, msftdata


Error: Invalid partition table - recursive partition on /dev/sdb.
Ignore/Cancel?

---

### Post by oldfred on 2018-03-23
What is sdb?
But that looks like a separate issue.

What brand/model system?

Did you manually partition?
System is UEFI with gpt partitioning, but your error is typical with trying to boot in one mode (UEFI or BIOS) and install is in other mode.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by nekoalosama on 2018-03-24
/dev/sdb is the USB I'm using for the live installer.

I am using a HP All-in-One - 20-c020 PC.

I did manually partition, using (if I remember correctly) 20GB for /, 25GB for /home, and 7.43GB for swap.

BootInfo report is [http://paste.ubuntu.com/p/p7KmRwWKnk/](http://paste.ubuntu.com/p/p7KmRwWKnk/)

---

### Post by oldfred on 2018-03-24
Since you do not have mount of ESP in fstab and have grub in MBR, you must have installed in BIOS boot mode.
With BIOS boot mode on gpt drives, you must have a tiny 1 or 2 MB unformatted partition with bios_grub flag for grub to correctly install. 

You can also convert existing install to UEFI by using Boot-Repair's advanced mode and the full uninstall/reinstall of grub2. That uninstalls the BIOS version and installs the UEFI version (and will add an entry to fstab to mount ESP). But you need to reboot live installer in UEFI mode, report says you booted in BIOS/Legacy/CSM mode. Boot-Repair may then offer that as a default fix. Also may need to turn off UEFI Secure Boot.
You may also have Windows fast start up on. That must be off for Ubuntu to see the NTFS partitions. When NTFS is hibernated or if it needs chkdsk, the Linux NTFS driver will not mount the NTFS read/write to prevent damage.

Some with HP do use BIOS as most HP systems do not make UEFI boot easy. It violates UEFI standard that says NOT to use description as part of boot. And only only valid description is "Windows Boot Manager".
But you have to then use UEFI boot menu to boot. Once you start booting in one mode or the other you cannot switch. Or grub can only boot other installs in the same boot mode as grub/Ubuntu is installed.

Many workarounds with HP, and I think a few lately have had it work. It is only the setting of ubuntu UEFI entry as default boot that does not work.
 Fallback/hard drive entry works, manually booting with UEFI like you have to with BIOS works. And then a BCD setting in Windows works as it is doing a one time reboot and in effect manually booting, but slower as booting into Windows first.

Now Boot-Repair automatically does copy to /EFI/Boot/bootx64.efi for UEFI hard drive boot.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 


       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---


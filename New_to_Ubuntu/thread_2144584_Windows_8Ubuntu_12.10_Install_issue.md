---
title: "Windows 8/Ubuntu 12.10 Install issue"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by parannoyed on 2013-05-12
I've loaded 3 or 4 other machines with various distros. I can usually fumble through everything fine, but I only know bare minimums.

Just bout an HP Envy with Windows 8 loaded on it. Loaded Ubuntu 12.10 on a usb to try and dual boot this machine. I've been through and disabled the secure boot and fast boot. Tried shrinking partition and tried making new partition both with no change in the end outcome. Ran easy bcd, restarted computer and chose to try ubuntu. Get into it fine, Run Gparted get everything set up and run Install. I choose language, next page I don't check anything, go to the next page, this is where I hit a brick wall.

It's showing me no partitions to choose from, no disk drives, nothing. The drop down menu shows me dev/sda2 (I think, running from a bad memory here) and allows no other options. I hit the next button and I'm met with:  "No root file system is defined."

Thats as far as I can get. I've tried some variations, reloaded everything, started from scratch 3 times. Nothing. I'd first like to have some idea what it is that is holding me back as I'd like to learn why it's not cooperating. Second, if I can't understand it, I'd still like to know how to fix it.

---

### Post by oldfred on 2013-05-12
Did you create partitions with Windows? It may have converted from basic to dynamic which does not work with Linux. And Windows knows nothing about ext4 partitions. You should create a shared NTFS data partition but use gparted.

Is this an UltraBook? The you have RAID from the Intel SRT.

 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)


 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

### Post by AndyOpie150 on 2013-05-12
How many partitions do you currently have on the hard drive and what are their formats?

This is what I usually do to install a dual boot from a flash drive.
With harddrive full of just one NTFS partiton with Windows on it I use Mini Tool Partition Wizard to split the partition leaving just 10GB more than the used amount for the Windows partition. I leave the rest as unallocated.
During the install from the USB flash drive I go to the advanced/something else partitoning option. 
I choose the unallocated partition. Leave the partition size set to as is. Select it to boot to /. Select to create.

If you need to cleanup the hard drive use Mini Tool Partition Wizard to delete all partions but the Windows. Format this to NTFS. Then Use EaseUS Partition Manager to merge the Windows partition with the now single large NTFS partition.
It will ask you to reboot to finish operation. When done rebooting several times you will have one solid clean partition again to start from scratch.

Note: Before starting, download and burn to a CD the "Boot Repair Disk.iso". Just in case you already managed to mess up your MBR and during the merge operation you are stuck in "grub rescue".

Hope this is helpfull.

EDIT: Ooops! Ninja'd by oldfred. Sorry bout that oldfred.

---


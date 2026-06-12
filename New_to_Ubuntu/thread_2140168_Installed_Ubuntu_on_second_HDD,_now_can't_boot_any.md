---
title: "Installed Ubuntu on second HDD, now can't boot anything"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by calcalocalo on 2013-04-28
Hello, I have been trying to get ubuntu 12.04lts running alongside windows 7 for quite some time now. I've tryed everything, installed in windows through an exe file, live booted and seperated partitions and then get grub working that way, but now I just gave up and bought a second hard drive reinstalled windows on the original and then when I went to install ubuntu on the other I lost the ability to boot into windows. It would do the loading windows when i choose windows bootloader from bios and then boot straight into ubuntu. I then removed the linux hdd from the boot order and when I tried to boot windows it said windows was unable to boot. Put the windows cd in and ran auto repair (didn't work) then ran "bootrec /mbr" which said was succesful and then "bootrec /fixboot" didn't work said no operating system or something to that nature. Now that I ran the fix mbr I'm not able to boot into anything! I did a live cd boot and tried to run the bootrepair. I get the following message, "You have installed on sda1 a Linux version which is not EFI-compatible. It is probably incompatible with your computer. Please install an EFI-compatible system. For example, Linux-Secure-Remix-64bit and Ubuntu-64bit are EFI-compatible systems." Which is false, I was running it well and installed many things to it before attemptimg to boot windows finding that it wouldn't boot. I then just choose to create a bootinfo summary from the boot repair application, here is the link.

[http://paste.ubuntu.com/5614454/](http://paste.ubuntu.com/5614454/)

I'm sure many of the things I did where stupid moves and have somehow majorly screwed up my boot order. I've been trying to get this sorted out for a week now and would much appreciate someone with some knowledge to take a look at my boot order and read that steps I've done and see if they could help me out. Help would be much appreciated. :)

My Computer:
Motherboard - Gigabyte z77x-d3h
Processor - intel core i5 3.4ghz
Video Card - Nvidia Gefource GTX 660

---

### Post by roywhite on 2013-04-28
I don't know if this is a solution, but I would try re installing ubuntu. If your system won't boot into grub, the linux install probably put the grub boot cmd in the wrong mbr. simpleist way to solve is to go into the bios and change disk boot order.

---

### Post by oldfred on 2013-04-29
You do need to reinstall Ubuntu on sda.

You have Windows in UEFI boot mode on gpt partitioned drive sdb 1TB.
You currently have Ubuntu in BIOS boot mode on a MBR(msdos) partitioned drive - sda 500GB. 

While you could dual boot by going into UEFI/BIOS and change to correct mode for install, that is a real hassle.

You have to have both systems as either BIOS boot or UEFI boot as each writes data to boot from differently.

Since Windows is UEFI, it is a lot easier to reinstall Ubuntu. And you need gpt partitioned drive which I would partition before install. Then be sure to boot from UEFI the Ubuntu installer in UEFI mode not BIOS mode. Since you have Windows 7, you can ignore all the comments on secure boot as you will not have that. It is so far only on new Windows 8 systems that are pre-installed. But still best to use newest version of Ubuntu as UEFI is still being upgraded. Also make sure your UEFI/BIOS is current as vendors also are changing a lot.

       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Others with two drive UEFI installs:
 Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---


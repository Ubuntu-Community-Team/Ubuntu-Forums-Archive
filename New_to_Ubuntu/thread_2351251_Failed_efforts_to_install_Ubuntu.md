---
title: "Failed efforts to install Ubuntu"
date: 2017-02-01
forum: New to Ubuntu
---

### Post by newmartin on 2017-02-01
[h=1]Problems with dual-booting[/h]
[LIST]
[*]Windows 10 is already installed.
[*]When booting with Ubuntu 16.4, 16.10 or Mint Cinnamon, GRUB won’t load Ubuntu or Mint on the hard drive I want. It doesn’t offer me the choice.
[*]Tried using Plop Boot Manager to boot from USB stick. GRUB tries to load Ubuntu onto USB stick and doesn’t offer me the choice of loading onto my desired drive.
[*]Any tips on how to install Ubuntu after receiving error messages gleamed from the Internet (YouTube, Geeks, Ubuntu website etc.) works for some of the steps to install, but there’s always a step which produces a result different from the one described.
[*]After searching the BIOS and the motherboard manufacturers, I was told in an email that the BIOS has no updates.
[/LIST]

Can anyone see the reason why Ubuntu isn’t loaded from the details below, and is it possible to find a way to load it? Your help would be greatly appreciated.

Martin
[h=1]Operating System[/h]Windows 10 Professional (x64) Version 1607 (build 14393.693)
Install Language:   English (United States)
System Locale:       English (United Kingdom)
Installed:                13/08/2016 23:28:01
Servicing Branch:  Current Branch (CB)
Boot Mode:             BIOS (Secure Boot not supported)
[h=1]Processor[/h]2.80 gigahertz AMD Athlon 64 X2 Dual Core 5400+
256 kilobyte primary memory cache
1024 kilobyte secondary memory cache
64bit ready
Multicore (2 total)
Not hyperthreaded
[h=1]Main Circuit Board[/h]Board:                    XFX MIA78S8209
Ver                         1.1
Bus Clock:             200 megahertz
BIOS:                     American Megatrends Inc. 080015 06/06/2008
[h=1]Drives[/h]1144.83 Gigabytes Usable Hard Drive Capacity
874.76 Gigabytes Hard Drive Free Space
HLDTST BDDVDRW CH10LS20 ATA Device [Optical drive]
3.5" format removeable media [Floppy drive]
[h=2]Drive 0[/h]ST3750330NS [Hard drive] (750.16 GB) rev SN04
SMART Status:      Healthy
[h=2]Drive 2 (Drive that I want  for Linux)[/h]ST3750330NS [Hard drive] (750.16 GB) rev SN04
SMART Status:      Healthy
[h=2]Drive 1 (Windows 10 drive)[/h]WDC WD5000AZLX00CL5A0 [Hard drive] (500.11 GB) rev 01.01A01
SMART Status:      Healthy

---

### Post by oldfred on 2017-02-01
You should not need plop, that would be for old systems that do not let you boot from flash drive, but only from CD drive.

But with Windows 10 you may have its fast start up on, which is hibernation.
And the Linux NTFS driver will not mount hibernated to prevent damage to the NTFS partition.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If installing to a second drive, you do need to use the something else install option. Only that option gives you to chance to install grub to the same drive. Other options install grub to drive seen as sda, which probably is your Windows boot.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---


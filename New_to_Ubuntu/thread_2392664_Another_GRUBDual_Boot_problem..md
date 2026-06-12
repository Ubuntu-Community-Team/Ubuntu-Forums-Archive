---
title: "Another GRUB/Dual Boot problem."
date: 2018-05-23
forum: New to Ubuntu
---

### Post by andrewaporter on 2018-05-23
[COLOR=#000000]Total newbie here.[/COLOR]
[COLOR=#000000]A few weeks ago I Loaded Ubuntu (14.?.?) dual boot on a Win 10 laptop. Initially I could boot into Ubuntu or Windows via Grub. Now Grub lets me into Windows but not Ubuntu. I get a blank screen with the cursor in the upper left corner.[/COLOR]

---

### Post by yancek on 2018-05-23
Were there any changes made just prior to this problem such as a major windows update?

---

### Post by andrewaporter on 2018-05-23
It seems MS updates Window every other day so probably.

---

### Post by oldfred on 2018-05-23
From Ubuntu live installer post this:
sudo fdisk -lu

---

### Post by andrewaporter on 2018-05-24
[COLOR=#000000]sudo fdisk -lu

no joy same results[/COLOR]

---

### Post by andrewaporter on 2018-05-24
Tried boot-repair without any improvement  

[http://paste.ubuntu.com/p/TCVN873QxW/](http://paste.ubuntu.com/p/TCVN873QxW/)

---

### Post by oldfred on 2018-05-24
I do not see anything out of order in report.

It looks like you have a newer UEFI system, but Windows 10 in BIOS boot mode on MBR partitioned drive.
Was this originally a Windows 7 system upgraded to Windows 10?

If you just installed probably better to have used 18.04 or at least 16.04 as they have many updates for newer systems.

---

### Post by andrewaporter on 2018-05-31
Thanks for the response oldfred.

The laptop is a "new" refurbished Win10 Acer.

I believe my initial post was inaccurate about the Ubuntu 14 load as I downloaded the lastest LTS at the time.

I made a portable USB Ubuntu 18 and can boot to it. This is would be acceptable solution, particularly if I could uninstall Ubuntu off the HD. Some questions though.

Could I do a new install over the old install.
Could/should I boot into windows (which still works) and delete the ubuntu partition(s) first.

Thanks

PS I've noticed that Grub also offers booting to Window on sda2 as well as sda1. Using the sda2 option gives required device missing error.

---

### Post by oldfred on 2018-05-31
Many users do not know that BIOS installs of Windows have a separate Boot partition and delete it.
And then the have not way to boot or even repair Windows as those same users have not made backups or Windows repair flash drives. So Boot-Repair copies essential boot files from Boot partition into main (c: drive) partition so at least it could be booted. And then grub finds boot files in both partitions and offers to boot Windows from either.

Windows 10 has fast start up which is just hibernation. Grub only boots working Windows or Windows that is not hibernated. And Windows will turn fast start up back on with updates.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Use Windows tools for Windows and Linux tools for Linux.
Or if deleting Linux partitions use gparted from Ubuntu live installer or a gparted live flash drive. If resizing NTFS partitions use Windows partitioning tools.

You have to reinstall the Windows boot loader to MBR before deleting any Linux partitions as part of grub is in Linux partition. Use your Windows repair disk or Installer's repair console.

I know newer Acer in UEFI boot mode require you to set UEFI password and set "trust" on .efi boot files. But in BIOS mode I do not think there is anything special with any system.

---


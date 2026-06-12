---
title: "Dual Booting with Win 7"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Mythblstr on 2012-12-22
I want to duel boot Ubuntu and Win 7 but I don't want to install Ubuntu on the same drive tha Win 7 is on. If I choose the installation option of "something else" and install the Ubuntu files on a different Hard Drive that has multiple NTFS partitions will it still automatically recognize Win 7 on the other Hard Drive?:p

---

### Post by cogier on 2012-12-22
If the "Other drive" is not the 1st drive the BIOS you may have issues.

If the "Ubuntu" drive is external or internal drive 2 I suggest you unplug the Win 7 drive (so Ubuntu will not see it). Install Ubuntu on the External or "drive 2" drive and then reconnect the Win & drive. This will prevent Ubuntu putting Grub on the Win 7 Drive.

You will then be able to use the Boot Options of any modern BIOS (usually F12) and select which drive to boot from. If you do nothing during a normal boot Win 7 will boot as normal.

---

### Post by audiomick on 2012-12-22
Yes. Be a bit careful; look carefully at what you are doing, but dont be scared of it.

You do know that you can't install ubuntu into an NTFS partition, don't you? You'll have to shrink to make room/ delete/ create a new partition. Sounds like you are not new to partitioning, though.


Incidentally: [COLOR="Red"]dual[/COLOR] boot. Duel sounds like a fight... ;)

---

### Post by audiomick on 2012-12-22
> **cogier said:**
> If the "Other drive" is not the 1st drive the BIOS you may have issues....


Shouldn't do. Mine doesn't. I have one install on an SSD and another, pre-existing install, on another, older drive. i.e. I added a drive and put another install on it.


I personally don't hold with unplugging drives during an install, but I know a lot of people do that. You have the option to tell the installer where to put the GRUB. I don't know exactly when it comes up, but it is there. I personally would just let it install it to the first drive. You are setting up a dual boot system. To me, that means having a boot loader that knows about all the installs on the system. If you should want to remove the Ubuntu install at some point and go back to just windows, it is possible to reconstruct the Windows MBR. It is not even hard to do... ;)

---

### Post by sandyd on 2012-12-22
Make sure the "boot loader" in the installation points to /dev/sda1. If you want, (this is very good if you have Bitlocker enabled with your windows 7), you can install the boot loader on your second drive instead.

You can then use EasyBCD to add Ubuntu to the Windows boot loader. :)

---

### Post by oldfred on 2012-12-22
With two drives, you just install grub2's boot loader to the Ubuntu drive. I always suggest making each drive totally independent. If not sure of install procedure you can disconnect drive. Ubuntu is tolerant of drive order changes now that it uses UUIDS.

But I always use Something Else or manual install and choose where to install grub2's boot loader (once I missed where to install grub and it overwrote wrong drive).

Grub2's os-prober will not have any issue finding installs on other hard drives. I have 4 drives and it finds all the installs. In fact I turn off os-prober and add my own commands as it takes a long time to scan 4 drives. :)

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Last link is to screenshot showing combo box with multiple drives & partitions to choose on where to install Boot loader. Same for gui installer. But only install to a drive not a partition.

Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Mythblstr on 2012-12-22
This .jpg is the current Hard Drive configuration on my XPS. I thought this might be complicated. I want to install Ubuntu over the XPPro partition and let it get reformatted to the Ubuntu native volume type. The trick here is that the XPro partition contains the Win 7 boot manager files (System partition in Microsoft's deluded terms). I'm not familiar with Bitlocker but I've used EasyBCD before. I can use that in the worse case scenario. Thank you for all the help ;)

---

### Post by oldfred on 2012-12-22
You need to move the Windows 7 boot files to the Windows 7 partition, add boot flag to Windows 7 partition, set BIOS to boot Windows 7 drive and run Windows 7 repairs to make sure everything is updated in BCD. And best to have Windows 7 repairCD or flash drive handy.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---


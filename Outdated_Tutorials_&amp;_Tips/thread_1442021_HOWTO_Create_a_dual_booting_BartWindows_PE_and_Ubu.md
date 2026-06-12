---
title: "HOWTO: Create a dual booting Bart/Windows PE and Ubuntu USB stick"
date: 2010-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by TimJC on 2010-03-29
[SIZE=2]**[COLOR=DarkRed]Purpose:[/COLOR]**[/SIZE]
My company has a Windows PE disk that we use to bypass hard drive  encryption in order to recover data should the OS become damaged.  I  have been using an Ubuntu LiveCD with DD_rescue and DD_rhelp to clone  damaged drives and grew tired of having to recompile or copy the  binaries to the bins directory, so I decided to create a USB stick with  both Windows PE and a persistent Ubuntu installation.  I couldn't find  anything on that net that explained the process so I pieced what little I  could find together to create this.  


**[SIZE=2][COLOR=DarkRed]Prerequisites:[/COLOR][/SIZE]**

[LIST]
[*]Windows PC
[*]USB  flash drive at least 2GB but no bigger than 4GB due to the FAT16  partition limitation.  You can use larger drives, but you will need to  use Gparted from the Ubuntu LiveCD to create a FAT16 partition up to 4GB  first. (WARNING: it will be formatted)
[*]Windows/Bart PE image
[*]PeToUSB  (creates a bootable FAT16 partition with Bart PE files) - [http://gocoding.com/page.php?al=petousb](http://gocoding.com/page.php?al=petousb)
[*]Ubuntu  ISO - [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
[*]Universal  USB Installer (handles the conversion from the Ubuntu ISO to the flash  drive)- [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)
[*]Bart's  mkbt.exe - [http://www.nu2.nu/mkbt/](http://www.nu2.nu/mkbt/)
[*]Bart’s  PE Builder - [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
[*]Latest  SysLinux ZIP file (boot loader editing) - [http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)
[/LIST]
**[SIZE=2][COLOR=DarkRed]Creating the BartPE Flash drive (10 minutes):[/COLOR][/SIZE]**

[LIST]
[*]Launch  PeToUSB.exe
[*]Select the flash drive you wish to use
[*]Enable disk format, quick format, and label the drive (PeToUSB  might crash if you try to format a drive larger than 4GB)
[*]Configure  the source path for the BartPE/WinPE files
[*]Enable file copy
[*]Click start
[*]Click yes to  continue
[*]Click yes to format the drive
[/LIST]
**[SIZE=2][COLOR=DarkRed]Installing Ubuntu onto the  flash drive (10-15 minutes):[/COLOR][/SIZE]**

[LIST]
[*]Open Universal USB  Installer (Universal-USB-Installer.exe)
[*]Agree to the militant  GNU/GPL license agreement
[*]Select the Linux distribution from the list (I used Ubuntu 9.10  Desktop i386)
[*]Click browse to select the Ubuntu ISO file (not  necessary if the ISO is in the same directory as Universal USB  Installer)
[*]Select your USB flash drive
[*]DO NOT check the  option to format the drive (this would overwrite the BartPE  installation)
[*]Select persistence option.  This is the file which  stores your settings and changes to Ubuntu on the drive (set to 1GB if  you have a 2GB drive or your choice on larger disks)
[*]Click  create
[/LIST]
**[SIZE=2][COLOR=DarkRed]Edit the Ubuntu boot menu so  there is an option to load your Windows/Bart PE installation:[/COLOR][/SIZE]**

[LIST]
[*]From  the mkbt ZIP copy mkbt.exe to the root of your flash drive
[*]From the Win32 directory of the SysLinux ZIP copy syslinux.exe  to the root of your flash drive (F:\ in this case)
[*]If you  haven’t already done so install PEBuilder
[*]Copy pe2usb.bin from  pebuilder’s installation directory  to the root of your flash drive  (C:\pebuilder3110a is the default installation location)
[*]Now  rename pe2usb.bin to pe2usb.bss (this is very important)
[*]Now  open command prompt
[LIST]
[*]Start>Run
[*]Type CMD
[*]Click  OK
[*]Change to flash drive’s drive letter (mine F: so yours might  differ)
[LIST]
[*]```
F:
```
[/LIST]
 
[*] Issue the following  commands (note: F: will be different if your flash drive uses another  letter)
[LIST]
[*]```
Mkbt –x pe2usb.bss F:
```
[/LIST]
 
[/LIST]
 
[/LIST]
```
Syslinux  F:
Exit
``` 
[LIST]
[*]Now copy pe2usb.bss from the root of your flash drive to the  syslinux directory.  For some reason I was able to get it to work with  pe2usb.bss on the root, but then it stopped.  Moving it to the syslinux  directory seemed to resolve the issue.
[*]Now navigate to the SysLinux directory on your flash drive  (F:\syslinux\ in my case)
[LIST]
[*]Open text.cfg with notepad (it will look messy to the naked eye  so make a new line anywhere you see a square  symbol)
[LIST]
[*]Between “default live” and “label live” add the following  lines
[LIST]
[*]```
Label BartPE
```
[/LIST]
 
[/LIST]
 
[/LIST]
 
[/LIST]
```
 menu label Windows/Bart PE
kernel pe2usb.bss
``` 
[LIST]
[*]
[LIST]
[*]
[LIST]
[*]Also add # to the beginning of the lines from “label  live-install” to “#initrd=/casper/initrd.gz splash --” (this will remove  the option for installing Ubuntu to hard disk, which would make data  recovery difficult)
[LIST]
[*]```
#label live-install
```
[/LIST]
 
[/LIST]
 
[/LIST]
 
[/LIST]
```
 #  menu label ^Install Ubuntu on a Hard Disk
#  kernel /casper/vmlinuz
#  append cdrom-detect/try-usb=true persistent
#file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  #initrd=/casper/initrd.gz splash –
``` 
[LIST]
[*]
[LIST]
[*]
[LIST]
[*]Save and close the file
[/LIST]
 
[*]Open syslinux.cfg with notepad
[LIST]
[*]Change the timeout from 300 to 0 (This will keep if from  auto-booting to Ubuntu after 30 seconds)
[*]Save and close the file
[/LIST]
 
[/LIST]
 
[/LIST]
 
[COLOR=DarkRed]**[SIZE=2]Eject the flash and trying  booting from it on a machine[/SIZE]**[/COLOR]

[LIST]
[*]Enjoy
[/LIST]
 
**[SIZE=2][COLOR=DarkRed]Sources:[/COLOR][/SIZE]**

[LIST]
[*]Dual Booting Slax Linux and BartPE (Windows) from a USB Thumbdrive  (UFD) [http://www.irongeek.com/i.php?page=security/dual-boot-slax-linux-bartpe-windows-usb](http://www.irongeek.com/i.php?page=security/dual-boot-slax-linux-bartpe-windows-usb)
[*]LiveUsbPendrivePersistent - Ubuntu Wiki [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[*]Install Ubuntu 9.10 to a Flash Drive from Windows [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)
[/LIST]

---


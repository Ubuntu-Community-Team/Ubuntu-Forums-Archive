---
title: "USB flash drive boot up stuck"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by gary75 on 2016-01-31
I'm a newbie to Linux, hence I chose this forum.

PROBLEM:  
When I try to run Ubuntu 14.04.3 from a bootable USB flash drive, the boot/process stays stuck at "Syslinux 4.03 2010-10-22 EDD Copyright ...."  My laptop is a new Lenovo B40-80 (Intel core i3), Windows 10.

WHAT I'VE DONE:
1) Changed the laptop's boot process from UEFI to Legacy, and insured that boot from USB is enabled.
2) Checked the laptop's memory with the Memtest86 v4.3.7, run from a bootable USB flash drive, confirming that the system indeed is booting from the USB port and that the memory on the laptop is okay.  Every aspect of the memory test succeeds.
3) Tried desktop Ubuntu 14.04.3 (as well as 13.10 and 15.10) on two different bootable flash drives each made from pendrivelinux.com as well as from UNETbootin ([http://unetbootin.github.io/](http://unetbootin.github.io/)).  I tried the 32 bit and 64 bit versions of each Linux release  (13.10, 14.04.3, 15.10) on each flash drive.  Every time I try to boot and run Ubuntu in these releases and versions installed as just noted on a USB flash drive, the result is the same as described in the PROBLEM. 
4)  Confirmed that Ubuntu 14.04.3, both in the 32 and 64 bit versions, WILL boot and run just fine when installed on a DVD and placed in a DVD drive connected to the same USB port I used for steps 2 and 3.

HELP!
I simply have no idea how to proceed from here in solving this problem.  Any input will be appreciated.

---

### Post by sudodus on 2016-01-31
Welcome to the Ubuntu Forums :-)

0. You need a 64-bit version of Ubuntu (amd64). I think you can try again with **ubuntu-14.04.3-desktop-amd64.iso**

Try in UEFI mode, because Windows is installed in UEFI mode.

1. Please check with ***md5sum***, that the downloaded iso file is correct. You can use ***md5summer*** in Windows.

See this link: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Try another tool to flash the iso file into the USB flash drive, for example [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows or [mkusb](https://help.ubuntu.com/community/mkusb) in linux.

---

### Post by Geoffrey_Arndt on 2016-01-31
Also, pls ensure Windows fast start/hibernation is turned off (as it's on in Win 10 by default), and it will ruin many a Linux install.

---

### Post by gary75 on 2016-01-31
I tried the Win 32 Disk Imager[COLOR=#000000]  on two flash drives as per your suggestion and Ubuntu runs fine from both drives.  Thank you!

Out of curiosity I tried the tool at [/COLOR][COLOR=#000000]pendrivelinux.com to flash the iso file into several USB flash drives.  On one drive Ubuntu ran fine and on the others the drive was completely ignored by the laptop's boot sequence.[/COLOR]

[COLOR=#000000]So ... my immediate problem is solved, though two questions remain ... should I perhaps create a new thread for each?[/COLOR]

[COLOR=#000000]1.  There is no way I see to create a "persistence" file with Win32 Disk Imager, which makes running Ubuntu from that flash drive a bit tedious, since all information must be entered after each boot, and nothing can be saved.  Am I right on this?  Any thought will again be appreciated.[/COLOR]

[COLOR=#000000]2.  I'm just curious why some flash drives work with the pendrivelinus.com tool, and others do not.  EDIT:  I just found the page "[/COLOR]Installation/FromUSBStick" which addresses my question.  If you have any additional thoughts, I'd value hearing them.  

[COLOR=#000000]Again, thanks for all your info!


[/COLOR]

---

### Post by sudodus on 2016-02-01
I'm glad it worked with Win32 Disk Imager :-)

You cannot create a file or partition for persistence in the same pendrive as the system, when cloned (via Win32 Disk Imager or any other tool) because it will get an ISO 9660 system which is read-only.

***Alternative 1.*** But you can create a file named 'casper-rw' or even better a partition labeled 'casper-rw' in another drive (another pendrive or HDD or SSD) with an ext2, ext3 or ext4 file system, which will be recognized and grabbed at reboot to get a persistent live system.

***Alternative 2.*** Now that you have a working USB flash drive with Ubuntu, you can install mkusb into it (yes only temporary, but it is enough), and use [mkusb](https://help.ubuntu.com/community/mkusb) to create a persistent live drive in another USB flash drive. You can also try the other methods described in [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), several of them are able to create persistent live drives.

***Alternative 3.*** You can even install an installed system in a USB flash drive (installed like 'installed into an internal drive'). Use the installer in the live system (the icon on the desktop) or select 'Install' directly at boot.

[hr][/hr]
See also the following links for more tips about USB flash drives alias pendrives alias thumb drives alias USB sticks :-)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

---

### Post by gary75 on 2016-02-01
Thank you! Merci beaucoup! Danke schön! :)

---

### Post by sudodus on 2016-02-01
You are welcome, and thanks for marking the thread as solved :-)

---


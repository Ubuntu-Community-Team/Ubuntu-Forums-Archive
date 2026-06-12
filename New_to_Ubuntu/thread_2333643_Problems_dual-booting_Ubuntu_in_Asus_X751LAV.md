---
title: "Problems dual-booting Ubuntu in Asus X751LAV"
date: 2016-08-11
forum: New to Ubuntu
---

### Post by fahem on 2016-08-11
Hey! I know I posted it in the wrong section that's because I am unfamiliar with the forum, hopefully moderators might move it to the correct section.

So lately, I have been trying to install Ubuntu alongside Windows 10 in my laptop Asus X751LAV. I used a disk imager to write the ubuntu.iso into the flash drive. So I plug the flash drive into PC, and restart it. When I do this, the loading time increases but it goes back to the regular old Windows I am using. Back to the loading part, I pressed keys such as ESC, F2 and F9 but nothing happens. 

I contacted Asus customer support but they told me they can't help me with installing any OS. 

I will be glad if you guys help me.

---

### Post by oldfred on 2016-08-11
Moved to New User.

Disk Imager does not sound like correct way to create a bootable flash drive.
Is Windows 10 installed in UEFI boot mode or an older upgrade of Windows 7 in BIOS boot mode?

Installers erase & format flash drive, extract & copy files in ISO to flash drive, and convert it or add boot files.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

Also how you boot install media UEFI or BIOS is then how it installs. You want Ubuntu in the same boot mode as Windows. So in UEFI/BIOS you have to select boot mode. If older BIOS it will only boot in BIOS mode.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---


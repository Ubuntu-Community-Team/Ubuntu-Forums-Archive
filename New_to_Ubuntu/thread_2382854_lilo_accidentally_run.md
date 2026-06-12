---
title: "lilo accidentally run?"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by tonyob on 2018-01-18
I tried to get lilo on a computer with internet to copy (by usb stick) to a computer with no internet (mbr problems on hard disk). So I did:

sudo apt-get install lilo

During the install a screen came up saying something like "Run liloconfig after reboot".  It might have said ldconfig, and maybe 'before reboot'. I hit the OK on the screen and the install finished. I figured it's just going to create the program and files ready to use, and not actually RUN the program. A search shows I have about 40 various lilo files in various places.

So did lilo run? Do I need to run liloconfig or ldconfig, and when?  Did I mess up the mbr? 

Judging from the numerous Grub files, I assume that's what was there before.  As I recall, the computer just boots directly to ubuntu (I have only one active partition), no grub/lilo menu, but generally I just leave my computer on.  I'll leave it on for now especially. 

The lilo documentation doesn't seem clear about all this, but that might be panic confusion.

---

### Post by Impavidus on 2018-01-18
If you want to download a package to transfer it it by usb stick to a different computer, try```
apt-get download [package-name]
```That should download the package (.deb file) and store it in the current directory, without installing it.

To make sure nothing changes on your computer, uninstall lilo and reinstall grub. How exactly may depend on how the computer was configured. On bios systems it should be something like```
sudo grub-install /dev/sda
```I don't know about newer UEFI systems as I use an older computer.

---

### Post by yancek on 2018-01-18
You would need to run "liloconfig" as root (use sudo) after the insntall.  It is similar to running update-grub for the Grub bootloader.  Why are you installing Lilo?  Maybe if you explained the problem with Grub someone would be able to help.

---


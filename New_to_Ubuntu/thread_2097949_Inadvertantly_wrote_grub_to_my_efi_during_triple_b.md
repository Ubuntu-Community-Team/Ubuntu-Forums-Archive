---
title: "Inadvertantly wrote grub to my efi during triple boot set up using refit."
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yeoracle on 2012-12-25
Hello everyone, 

I just recently converted my macbook pro 5,4 into a triple boot system with window 7, and Linux Mint. During the process I incorrectly wrote the bootloader to /dev/sda. I've completed my setup and all os's are functioning properly except that when I boot up to my refit menu screen, I have two linux icons.  One that points to my linux installation and one that points to the linux  on my efi partition. The icon pointing to linux on my efi partion just hangs up during the boot process when I use it. The other icons to windows, mac, and linux, boots to those systems. I've tried to make a gparted live cd unsuccessfully. Can't get the mac to boot from the live cd iso's. Not sure why. Verified the checksum and they checked but cant get the mac to boot to the cd or the usb. Tried burning the iso, converting the iso to dmg and img. What I would like to know is, if there is a way to remove the grub entry from my efi partition without having to do a clean install of my mac software?
Thanks for your consideration.

---

### Post by gonzoks on 2013-01-01
If you can get into your MacOS (sorry, but am a little unclear if you can or not based on your post), do you know if reinstalling reFit forces the system into seeing the proper OS selections?  I recently did this and had to blast reFit off of the system and do the standard 2-3 reboots before all was happy again.  YMMV, obviously.

---

### Post by Yeoracle on 2013-01-02
Thanks for the response Gonzoks. Sorry for the ambiguity. I'm running osx 10.6.8 on a macbook pro unibody 5,4. I'm able to boot the system in all three operating systems. (Windows 7, Linux Mint and Os x). The problem that I'm having is with the refit menu list showing an additional Linux Icon for the EFI partition. I'm assuming that I've installed some grub info on that partition for the icon to show as a Linux boot through the EFI partition on my refit menu list. When I uninstall refit my system reverts back to booting directly into my mac os as normal but once I reinstall refit the Linux icon reappears for the EFI partition at the refit menu list.  Any suggestions on where I should focus my search to correct this would be appreciated.

---


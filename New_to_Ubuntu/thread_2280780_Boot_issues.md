---
title: "Boot issues"
date: 2015-06-02
forum: New to Ubuntu
---

### Post by james142 on 2015-06-02
Hey, im totally new to ubuntu and have used it as a last resort style thing because my new PC build refused my windows 7 install.

I can access my bios and still have the live usb with ubuntu ready to reinstall in needed.

When i installed it seemed stuck on a screen with a purple/yellow gradient for about 10 minutes at which point i hard reset my PC and tried to boot (as the installation bar filled and closed the window itself leaving me on the above mentioned screen) from the HDD i installed ubuntu 14.04 on however when i boot from the HDD i only get a dark purple screen with nothing on it and when this goes i get no signal from either monitor (currently have 2 connected but all of this is only happening on 1 screen).

Apart from when the screen didnt change for 10-15 minutes i think the installation went well. Any help is much appreciated as ive been having problems with this PC since it was built. (Audio cables burning, corrupt bios and not enough clearance for my CPU cooler to name a few)

---

### Post by oldfred on 2015-06-02
What motherboard, cpu & video card.
Video issues are common and often nomodeset boot parameter is required.

Also is system UEFI or BIOS. If new system it really is both and you have to choose when you boot which way you want to install. How you boot installer for both Windows & Ubuntu is then how it installs. Windows 7 default is BIOS, but can be copied to a flash drive and efi files moved to make it UEFI bootable.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---


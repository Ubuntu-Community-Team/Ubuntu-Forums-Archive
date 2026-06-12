---
title: "Installation stuck in BIOS - UBUNTU v. 14.04 desktop @ TOSHIBA C660-1CW"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by Majo13 on 2014-06-27
Hello guys,

this is going to be my entire first post in this forum, so let's get started.

Hardware info:
[http://www.toshiba-slovakia.com/discontinued-products/satellite-c660-1cw/](http://www.toshiba-slovakia.com/discontinued-products/satellite-c660-1cw/)

Software info:
I've created a bootable UBUNTU v. 14.04 USB drive with help of Universal-USB-Installer-1.9.5.3.

After that, i restared my laptop, went to the booting menu. 
I've choosen " boot from USB kingston drive.

Booting proccess started right after. I've read somehwere, that if u want to get to the installation menu of UBUNTU
u'll be able to do that, only by hitting a random key, so i did.
This action transported me to the installation menu, where i could choose an option of installing UBUNTU.

On the first try, i've choosen INSTALL UBUNTU, with no luck, screen was stuck in a textful screen.

On the second try, i've hit F6 to disable all addons, so i did. 
Result was, that i was again at some textful screen that was stuck again.

This is the screen, it was stuck at. ( apologizing for the glossy screen, my bad, if needed, i'll recapture the screen )

[IMG]http://i.imgur.com/skQk1ON.jpg?1[/IMG]

Could someone of u give me some advice, where to look at or what should i try ?

---

### Post by oldfred on 2014-06-27
I do not know AMD as I have nVidia, but try several boot options.
At accessibility icons (the tiny person & keyboard at bottom of screen) press any key, then f6.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

some also try these:

 

[LIST]
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

But your specific system may need other/additional boot parameters.
Is BIOS set for AHCI not IDE?

---

### Post by Majo13 on 2014-06-27
Thank you, will investigate and post a result.

---


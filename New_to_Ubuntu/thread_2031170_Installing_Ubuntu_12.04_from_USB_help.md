---
title: "Installing Ubuntu 12.04 from USB help?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by itzdarockz on 2012-07-21
I am trying to install ubuntu 64 bit via USB but it doesnt seem to be working. Whenever I get into BIOS my USB comes up as FDD instead of USB. Than when I boot from FDD a black screen comes up showing a statement (I don't remember what it says). The USB was fully formatted when it was installed and I also checked for errors before it was installed. I am using FAT32 as the file system and a 4GB Gigaware USB. Thanks.

---

### Post by Autodave on 2012-07-21
> **itzdarockz said:**
> I am trying to install ubuntu via USB but it doesnt seem to be working. Whenever I get into BIOS my USB comes up as FDD instead of USB. Than when I boot from FDD a black screen comes up showing a statement (I don't remember what it says). The USB was fully formatted when it was installed and I also checked for errors before it was installed. I am using FAT32 as the file system and a 4GB Gigaware USB. Thanks.


Did you make the USB stick bootable?  You cannot just copy the file to the USB stick.

---

### Post by itzdarockz on 2012-07-21
> **Autodave said:**
> Did you make the USB stick bootable?  You cannot just copy the file to the USB stick.

Yes I did. I used Universal USB Installer v 1.9.0.4.

---

### Post by Shadius on 2012-07-21
If you're using Windows to create a LiveUSB, here's a link to check out: [Create a USB stick on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by itzdarockz on 2012-07-21
> **Shadius said:**
> If you're using Windows to create a LiveUSB, here's a link to check out: [Create a USB stick on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

I did exactly what it said to do but no good. I saw this before and yea im using windows 7.

---

### Post by oldfred on 2012-07-21
You may be getting the video issue. Is your system nVidia, but it may be with other systems also.

With a CD you click on any key at the very beginning when the accessibility icons show at the bottom.

Some say tab works with the USB boot:
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'

I boot USB differently with grub2 and have always added nomodeset to the the grub entries, but you can do something similar with syslinux the boot loader on the liveUSB. Example in blog is for gma500, but you can use any boot parameter you need.
If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by itzdarockz on 2012-07-21
> **oldfred said:**
> You may be getting the video issue. Is your system nVidia, but it may be with other systems also.

With a CD you click on any key at the very beginning when the accessibility icons show at the bottom.

Some say tab works with the USB boot:
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'

I boot USB differently with grub2 and have always added nomodeset to the the grub entries, but you can do something similar with syslinux the boot loader on the liveUSB. Example in blog is for gma500, but you can use any boot parameter you need.
If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

My system is actually amd.

---

### Post by oldfred on 2012-07-21
I think nomodeset works for most.

These were older settings which may work. Some find generic also works regardless of video card.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by yuvraj23 on 2012-07-22
Ya I too had the problem when installing via USB.. I made my pendrive bootable using an application called unetbootin. It worked fine....

---


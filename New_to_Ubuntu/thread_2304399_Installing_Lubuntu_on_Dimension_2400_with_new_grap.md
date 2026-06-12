---
title: "Installing Lubuntu on Dimension 2400 with new graphics card"
date: 2015-11-26
forum: New to Ubuntu
---

### Post by gary71 on 2015-11-26
Let me start by saying I'm completely new to Ubuntu. I have an old Dell Dimension 2400 with 2gb of ram on which I'm trying to install Lubuntu.  After googling a bit and seeing that the onboard graphics on this computer won't cut it, I put in a GeForce MX400 hoping that would do the trick. No luck. I'm trying to install from a a USB drive and when I start computer, boot from USB, I get the Lubuntu menu (run without installing, install, advanced options, etc.) but that's as far as I can go. If I choose run without installing, I get a blurry beige screen with a blinking cursor. If I choose install, I get a blank screen. 

I'm assuming it perhaps has something to do with lack of driver for card?  Can someone give me some advice?  As I said, I'm new to Unbuntu so would appreciate very simple directions. :Da

Thanks.

---

### Post by grahammechanical on 2015-11-26
Here are the minimum requirements for Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

We need more RAM for the installation process than we need to actually run the OS

> The default "Desktop" installer requires 384-800 MB  of RAM (depending on selected options.)  If you have problems, please  use the [alternative installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). 



Even so, we may still need to change a boot option for the installer to get a live session. See this wiki page and the section: Changing the CD's Boot Options. Go to Section 6 - F6 and set nomodeset.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

There is another thing to consider. During installation we are asked if we want to install third party software. Tick that box and you will get a proprietary video driver and it will be the latest stable version from the software repositories of the version of Lubuntu that you are installing. The latest Nvidia drivers will not support that graphic adapter. I have an Nvidia adapter much newer than your adapter and it is not supported by the latest Nvidia drivers. 

[http://www.cnet.com/products/nvidia-geforce2-mx400-agp-4x-32mb/specs/](http://www.cnet.com/products/nvidia-geforce2-mx400-agp-4x-32mb/specs/)

If we do not tick the box "Install third party software" we get an open source video driver. The live session runs on the open source video driver. So, if we can get a live session running, then we should at least get to a working desktop after installation has completed.
 
Regards.

---

### Post by ajgreeny on 2015-11-26
You have more than enough ram for installing and running Lubuntu, so I think we can forget about that as a potential problem for now.
I do agree that you should run the live installer with the **nomodeset** boot-option by pressing F6, and that should get you to a GUI desktop, even if it's at a low resolution; you should then be able to install from there.

I never ask for updates and proprietary drivers to be installed when I am installing the OS; I prefer to have the control of that later once it's up and running, but I have never had an nvidia graphic card to need such a driver, so I can't really help with that.

---

### Post by mörgæs on 2015-11-26
MX400 is a very old card. Here is some advice:
[http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687](http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687)

but you will be better off if you can get something a little faster.

---


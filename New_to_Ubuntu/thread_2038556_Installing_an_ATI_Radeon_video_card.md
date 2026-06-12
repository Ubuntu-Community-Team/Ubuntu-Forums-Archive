---
title: "Installing an ATI Radeon video card?"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by zuren on 2012-08-06
I've been digging around trying to figure out if an ATI Radeon 7500 PCI graphics card is supported and can be used on this older system running Lubuntu.  I have found a couple threads discussing the general idea but not Lubuntu specifically and I'm not clear on how to get it done.

Resources I've found:
1.  [http://ubuntuforums.org/showthread.php?t=1398533&highlight=radeon+7500](http://ubuntuforums.org/showthread.php?t=1398533&highlight=radeon+7500)

2.  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

3.  [http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html)

Right now I'm running off of the onboard Intel controller.  When I plug into the ATI card, I get nothing so it is clearly not installed.  I ran the command:
> lspci -nn | grep VGAThe ATI card is being recognized.  I also see under PCI Devices:
> [COLOR=Blue]-PCI Devices-[/COLOR]
[COLOR=Blue]Host bridge        : Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)[/COLOR]
[COLOR=Blue]VGA compatible controller        : Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03) (prog-if 00 [VGA controller])[/COLOR]
 [COLOR=Blue]PCI bridge        : Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])[/COLOR]
[COLOR=Blue]ISA bridge        : Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)[/COLOR]
 [COLOR=Blue]IDE interface        : Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])[/COLOR]
[COLOR=Blue]USB controller        : Intel Corporation 82801AA USB Controller (rev 02) (prog-if 00 [UHCI])[/COLOR]
 [COLOR=Blue]SMBus        : Intel Corporation 82801AA SMBus Controller (rev 02)[/COLOR]
[COLOR=Blue]Ethernet controller        : Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)[/COLOR]
 [COLOR=Blue]USB controller        : NEC Corporation USB (rev 41) (prog-if 10 [OHCI])[/COLOR]
[COLOR=Blue]USB controller        : NEC Corporation USB (rev 41) (prog-if 10 [OHCI])[/COLOR]
 [COLOR=Blue]USB controller        : NEC Corporation USB 2.0 (rev 02) (prog-if 20 [EHCI])[/COLOR]
[COLOR=Blue]Multimedia audio controller        : Creative Labs SB Live! EMU10k1 (rev 07)[/COLOR]
 [COLOR=Blue]Input device controller        : Creative Labs SB Live! Game Port (rev 07)[/COLOR]
[COLOR=Blue]VGA compatible controller        : Advanced Micro Devices [AMD] nee ATI RV200 QW [Radeon 7500] (prog-if 00 [VGA controller])[/COLOR]
So the system is definitely seeing it.  Should I be using link #2 above as my guide to get this installed, if it's possible?

Thanks!

System:
Dell Dimension L866R tower (circa 1999)
Pentium III 866MHz
256MB RAM (soon to be 512MB max-ed) 
4+1 USB PCI card
Soundblaster Live PCI sound card
Dynex NIC PCI card
Intel 82810E Graphics Controller (monitor currently connected to this)
ATI Radeon 7500 video card (installed but not working; also have a Voodoo2 in a box)
now running Lubuntu 12.04

---

### Post by z3nhakr on 2012-08-06
have you checked for additional drivers using jockey?

---

### Post by zuren on 2012-08-06
> **z3nhakr said:**
> have you checked for additional drivers using jockey?

If jockey is the tool under Preferences > Additional Drivers, I ran it.  It searched for additional drivers and came back with:

> No proprietary drivers are in use on this system

---

### Post by z3nhakr on 2012-08-06
the driver is already packaged with ubuntu. you can switch to the ati card by modifying your xorg.conf file located in "/etc/X11/"

---

### Post by mastablasta on 2012-08-07
ATI dropped Linux support for this card quite some time ago.
 
if by "i get nothing" you mean you can't boot into live session, perhaps you needto use nomodeset or another boot parameter.
 
the available opensource drivers are included in kernel and should work with your card:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
it should even have 3D acceleration support.

---

### Post by zuren on 2012-08-07
> **mastablasta said:**
> ATI dropped Linux support for this card quite some time ago.
 
if by "i get nothing" you mean you can't boot into live session, perhaps you needto use nomodeset or another boot parameter.
 
the available opensource drivers are included in kernel and should work with your card:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
it should even have 3D acceleration support.

I have 2 monitor connections on the back of this box.  One is for the onboard Intel graphic controller (VGA).  The other is the ATI card that has VGA, DVI and S-video.  By "get nothing" I mean that when I connect the monitor to the ATI card, there is zero signal despite Lubuntu seeing the hardware.  I'm able to see everything when connected to the onboard connection.

It looks like I need to get the right driver active.

---

### Post by mastablasta on 2012-08-08
or disable intel
or edit xorg.conf, so that it recognised both chips.

---

### Post by deadflowr on 2012-08-08
Can you switch the video control settings in the bios? I find this typically happens, and I have to enter the bios and then find the video setting area and switch the setting from the default on-board to PCI or APG or PCI-E.
If you've already tried this, chances are the card is junked. Sadly it happens, cards can die.
I mention this because it seems like you're not getting any signal from the card at all. Usually you'd get some kind of signal and at the very least astoundly horrible resolution.

---

### Post by zuren on 2012-08-09
> **deadflowr said:**
> Can you switch the video control settings in the bios? I find this typically happens, and I have to enter the bios and then find the video setting area and switch the setting from the default on-board to PCI or APG or PCI-E.
If you've already tried this, chances are the card is junked. Sadly it happens, cards can die.
I mention this because it seems like you're not getting any signal from the card at all. Usually you'd get some kind of signal and at the very least astoundly horrible resolution.

That was it!  I can't believe I overlooked that but the card is now working and using the DVI connection, looks great.  Thanks for the tip!

---


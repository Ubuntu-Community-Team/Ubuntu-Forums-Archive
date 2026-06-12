---
title: "my graphics crashed- compizfusion"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-06
from the beginning:   
  what I had was green text on black entry fields.  and rain drops from water effects.  Now the rain drops only display over open windows and my detop panels.  not the destop field itself.  this is aggravating because it did work.  also I have no ability to adjust color settings for font or entry fields (wherever you would type)  I still have desktop color settings.  anothing thing to note is that when things got strange i had previously messed around in advanced desktop settings.  and I also tried to install conky to no avail but when i was attempting to do so (take the black off the desktop)  it was shortly after that.  I have since performed complete removal of conky.  but the color is still lost and the raindrops (an absolute necessity) are not displayed over destop.  help.

---

### Post by DM was on fire! on 2008-06-06
If you're running Compiz, turn off Desktop Effects (I believe that's what it's called) and turn them back on.
If that doesn't work, perhaps try a fresh install of Compiz?

---

### Post by adamogardner on 2008-06-06
when you say turn them off do you mean uncheck the little box or is it something alltogeter different?

---

### Post by Duck2006 on 2008-06-06
Yes

---

### Post by DM was on fire! on 2008-06-06
> **adamogardner said:**
> when you say turn them off do you mean uncheck the little box or is it something alltogeter different?

I *assume* the checkbox.
I'm actually not running Compiz, I'm just going on what I've seen other people say. XD

---

### Post by adamogardner on 2008-06-06
ok i did that well before.  what kind of headache does it require to reinstall    you have a command or two for me?   any idea what I did in the first place?

---

### Post by DM was on fire! on 2008-06-06
I think you should be able to put this into Terminal:

```
sudo apt-get --reinstall install compiz-fusion
```

Or whatever the name if the package is (you can always check in Synaptic).

---

### Post by Duck2006 on 2008-06-06
You find it in Synaptic Package Manager.

---

### Post by DM was on fire! on 2008-06-06
> **Duck2006 said:**
> You find it in Synaptic Package Manager.

Yeah, that's the easier way to do it. XD
I just run apt-get because it doesn't slow my computer down.

---

### Post by adamogardner on 2008-06-06
ok well i reinstalled from synaptic because there was a long line of numbers and such and there was more than one package (2 actually)  then my graphics got real real sluggish.  so I restarted.   sluggishness is gone  but all the same problems remain.  ARGHH

---

### Post by DM was on fire! on 2008-06-06
> **adamogardner said:**
> ok well i reinstalled from synaptic because there was a long line of numbers and such and there was more than one package (2 actually)  then my graphics got real real sluggish.  so I restarted.   sluggishness is gone  but all the same problems remain.  ARGHH

Hmm.
Reinstall again and try to paste the output?

---

### Post by adamogardner on 2008-06-06
no there was no output because I reinstalled from synaptic sine there were more than one package and the names had long line of numbers following them.   I'll try it from terminal.  and paste the output  but as far as I can tell and the computer indicated to me the installation was a success. by closing dialog box after successful completion.   be right back

---

### Post by adamogardner on 2008-06-06
says invalid operation compiz-fusion   must I add all those numbers?

---

### Post by DM was on fire! on 2008-06-06
Ah, that's right. You uninstalled via Synaptic.
Apologies for that. ^^;;

EDIT - Huh, that's weird.
Sadly, I don't know how much I can help now. 
But, on a random chance...what video card are you running?

---

### Post by adamogardner on 2008-06-06
whats a video card?  It came inside my laptop  sticker says graphics by nvidia   I have a Pavillion DV6700  IT's a handsome machine   and whatever the case it all worked once before.

---

### Post by Duck2006 on 2008-06-06
> whats a video card? It came inside my laptop sticker says graphics by nvidia

The video card is a nvidia, any numbers after the name nvidia, you may have to load restricted extras.

---

### Post by philinux on 2008-06-06
Post the output of

[FONT="Courier New"]lspci[/FONT]

thats an L at the beginning

---

### Post by adamogardner on 2008-06-06
i have (according to synaptic).. linux-restricted-modules 2.6.22.4-14.10   and nvidia-glx-new 100.14.19+2.6.22   and   nvidia-kernal-common 20051028+1ubuntu   and  restricted-manager 0.33.1  and   restricted-manager-core 0.33.1   please understand I don't know what restricted extras are let alone what load means.  but I'm on it!
  
   and here is lspci:adamogardner@CRONUS:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by Duck2006 on 2008-06-06
> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)

This is your video card.

This may help.

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

### Post by SteveNorman on 2008-06-06
do system>admin>hardware settings and see if you have an nvidia driver installed,,if you do make sure the box is checked. If you dont you will need to load a driver for it.

Se starcannons post:

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by adamogardner on 2008-06-06
WHOA!  I don't have hardware settings under sys>admin...keeping in mind it all worked once before.  how do I add the hardware settings to my admin. menu?

---

### Post by SteveNorman on 2008-06-06
first install nvidia-settings

```
sudp apt-get install nvidia-settings

```
then in terminal type nvida-settings

look around in there for a driver, server settings I believe

see if you have a driver,,if not you will have to do the long install via starcannon's instructions in the post I linked earlier

---


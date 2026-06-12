---
title: "Wireless on Omnibook 500 not working, 8.10"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Enigman on 2008-11-17
I just did a fresh install of 8.10.  Laptop runs well, Kubuntu comes up but does not seem to recognize wireless.  This is an old Omnibook 500 that I'm trying to convert to Kubuntu.

Though I've been using Ubuntu and Kubuntu for a couple years (not on this laptop), I'm a newbie to the command level of things.  I  hope to learn by trying to get this working.  I appreciate all the help.

---

### Post by bumanie on 2008-11-17
Post the output of > lspciThis will list your wi-fi card. Once known, you can see if there is a driver for it or as a last resort, try ndiswrapper.

---

### Post by Enigman on 2008-11-17
Here you go.  I appreciate the help.  The HP website says this has an Actiontec prism integrated (USB) 802.11b wireless lan.

:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone](rev 10)
00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

---

### Post by greed$$$ on 2008-12-18
I have the same problem and the same output when i run lspci. Looks like it does not see or it is not turned on. I do see wlan0 in the network manager but cannot get it to work and i notice there is not mac address. How do i turn it on.

---

### Post by bumanie on 2008-12-19
Post the output of>  lshwHopefully that will list the card - if it's a very new card, it may not be in the kernel as yet.

---

### Post by bumanie on 2008-12-19
Some googling brought me to this page - [http://sourceforge.net/projects/orinoco/](http://sourceforge.net/projects/orinoco/) apparently the lucent card you have works with this driver.

---

### Post by greed$$$ on 2008-12-30
So I did find that it does see the card when i do an lspci it lists pci stuff
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
00:11.0 IDE interface: Silicon Image, Inc. PCI0648 (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

When i do lsusb is see it
Bus 001 Device 003: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 001 Device 002: ID 03f0:2002 Hewlett-Packard Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I see it as an option in network manager but it never works. So i loaded ndiswrapper and downloaded the XP drivers from hp and got the inf and sys file. I then point ndiswrapper to the file and it took it. then when i went to config the network it would say could not find network  configuration tool. So i rebooted and then it hung trying to load blue tooth so does not look like i got the right driver. I could not get past the stuck bluetooth boot up so I had to reload ubuntu. I am still new to this and it is quicker for me to reload the pc than to fix it since I still not sure what i am doing. Any help would be great thanks.

---

### Post by greed$$$ on 2009-01-03
I was able to use the ndiswrapper with the drivers from the hp website and i was able to see my wireless. YEAAAA. I then went to set it up cause am using wep 64bit. Put in the key and all that and it was unable to connect. I kept trying making sure i typed the key correctly. I then turned off wep and just had wide open wireless. I conntected and the system locked up. Looks like it need to try diff drivers or something but at least i got closer.  My router is a Linksys WRT54G running DD-WRT v23

---


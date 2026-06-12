---
title: "(another) wireless connection problem"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ben123 on 2008-08-25
hi, (as a side note i installed ubuntu yesterday, hence the stupidity)

i have an acer 5715z and sky wireless BB, with a netgear router (not sure what model, it doesent say on the bottom) it has a WEP network key, 128 bit, (hex. i think, im not really sure), anyway, the icon in the taskbar (at the top) on ubuntu for connecting to networks, when clicked on it doesent list the network so i enter the network name and key, it says "attemting to connect" and then asks me for the network key again, it stops attemting to conect after a while and it isnt connected (obviously), then last night the icon i clicked on disappeard and i cant get it back



i just realised how confusing that is, sorry, help if you can, i hate having no internet....   :neutral: :neutral: :neutral:

---

### Post by anewguy on 2008-08-25
Well, I can think of a couple of things first:

(1) Did you install a driver for your wireless adaptor?  What is the maker/model of your wireless adaptor?  Try "lspci" in a terminal window and post the output back here.

(2) Under System/Administration/Network does "Wireless" show?  Is roaming mode enabled?

Post those back and we can go from there.

---

### Post by ben123 on 2008-08-25
yes "wireless" does show and roaming is enabled,
this is the stuff from the terminal:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) 
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by Gone fishing on 2008-08-25
I find that sometimes roaming works well but often it doesn't, so I would try turning roaming off and using the Network manager  (System>Administration>network) and setting up your wireless there.

If you still have a problem The config file is /etc/network/interfaces you can check every thing is as it should be.

mine looks like I'm using WEP encryption and a static IP:

to lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:qxxxxxxxxxxxx
wireless-essid fish

auto wlan0

the s: before the password shows that the password is an ascii phrase.

Oh and ascci would look like passwsord = mypasswordisa 
Hex = 6d 79 70 61 73 73 77 6f 72 64 69 73 61

---

### Post by ben123 on 2008-08-25
ive trieturning off roaming and setting it up that way, nothing happened, how do u get to the config file? as i said, i really am a newbie to linux/ubuntu

---

### Post by Gone fishing on 2008-08-25
open a terminal and run the following commands:

gedit /etc/network/interfaces and if you want to change the file sudo gedit /etc/network/interfaces

---

### Post by ben123 on 2008-08-25
thanx, unfortunately ive been told to uninstall ubuntu from my laptop (technically not my laptop)but i should be putting it back on soon, thanx for your help anyway

---


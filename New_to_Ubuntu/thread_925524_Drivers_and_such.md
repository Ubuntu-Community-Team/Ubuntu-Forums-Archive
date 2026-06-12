---
title: "Drivers and such"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by heylookbjsgay on 2008-09-20
I just installed Ubuntu on my acer 4420-5239 laptop and the wireless is not working. There's a switch in the front to turn it on and when I slide it, Ubuntu does nothing. My sound does work, I think lol. And my desktop effects couldn't be turned on I think because of my graphics driver, it prompted me to enable the driver and it said installing and I got a 404 error the file wasn't found. If someone could help me out on these 2 issues it would be very much appreciated. Thank you!

PS: Sorry I'm a noob at Ubuntu :P

Acer extensa btw.

---

### Post by overdrank on 2008-09-20
> **heylookbjsgay said:**
> I just installed Ubuntu on my acer 4420-5239 laptop and the wireless is not working. There's a switch in the front to turn it on and when I slide it, Ubuntu does nothing. My sound does work, I think lol. And my desktop effects couldn't be turned on I think because of my graphics driver, it prompted me to enable the driver and it said installing and I got a 404 error the file wasn't found. If someone could help me out on these 2 issues it would be very much appreciated. Thank you!

PS: Sorry I'm a noob at Ubuntu :P

Acer extensa btw.

Hi and welcome, yes you will need internet access to enable the driver for your graphics card. Can you access a wired connection? Also you can use the command ```
lspci 
``` in the terminal located under applications, accessories. and this will identify your hardware and then you can search for info to help solve the issues. 


Moved to ABT :)

---

### Post by heylookbjsgay on 2008-09-20
I am on wired.

dillon@dillon-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
dillon@dillon-laptop:~$ 


That's what I get, Thank you!

---

### Post by heylookbjsgay on 2008-09-20
I read my network driver wasn't compatible somewhere. :confused:

I hope this isn't true :(

---

### Post by heylookbjsgay on 2008-09-20
So it seems it's trying to grab the file off the site that isn't there?

---

### Post by overdrank on 2008-09-20
Hi and I had a acer laptop and had no issue with the wired connection but with the wireless was another issue. If you have no internet connection on the laptop then it will get a error.

---

### Post by mikewhatever on 2008-09-20
The site is there, just get the network sorted first.

---

### Post by heylookbjsgay on 2008-09-20
lol, I am on wired.
That's how I'm here.
:P

Holy  lol
119 updates detected... o_O

---

### Post by overdrank on 2008-09-20
> **heylookbjsgay said:**
> lol, I am on wired.
That's how I'm here.
:P

Holy  lol
119 updates detected... o_O

Then you may look at changing the server location under system, administration, software sources.

---

### Post by heylookbjsgay on 2008-09-20
Okay, thank you that did end up working for the graphics thing.
Sorry for the language up there, lol.

---

### Post by heylookbjsgay on 2008-09-20
Now can anyone help with my wifi? :D:D

Someone recommended madwifi and I'm in the proccess of installing that...

---


---
title: "Ubuntu hardy Dell 1350 wireless problem"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by nsolo on 2008-07-19
I'm dual booting to the "Hardy" version of Ubuntu. My Dell 1350 wireless card will not even show a working light let alone work. It works fine in XP.

It says that no proprietary drivers are to be found when I do into Administration-Hardware.

Newbie isn't a strong enough word to describe my abilities with this Ubuntu, so talk down to me when giving direction.

All else seems to work fine. Wired internet is ok. Wireless is not.

---

### Post by XVII on 2008-07-19
Go to the dell website and download the driver for your card.  Save it to your desktop.

I suggest you get ndisgtk:

```
sudo apt-get update && sudo apt-get install ndisgtk 
```

Then in the terminal type:

```
unzip ~/Desktop/the_exe_file
```

and then:

```
ndisgtk
```

Load the .inf file that you extracted from the .exe file.

Make sure the driver is installed by putting this in your terminal:

```
ndiswrapper -l
```

---

### Post by dodle on 2008-08-27
[QUOTE=XVII]Go to the dell website and download the driver for your card. Save it to your desktop.

I suggest you get ndisgtk:[/QUOTE]

I am having the exact same problem with the exact same card.  I tried XVII's suggestion but cannot get it to work.  Does anybody know how to resolve this.  Ndisgtk has worked for me with other cards, even generic ones.

---

### Post by Ryadt on 2008-08-27
> **dodle said:**
> I am having the exact same problem with the exact same card.  I tried XVII's suggestion but cannot get it to work.  Does anybody know how to resolve this.  Ndisgtk has worked for me with other cards, even generic ones.

Post the ouput of ```
lshw -C network
```

---

### Post by anewguy on 2008-08-27
Please also include the output of lspci.

---

### Post by dodle on 2008-08-27
I unhooked my wired connection to run these commands.  I didn't know if they would be affected.

```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 03
       serial: 00:90:96:b5:4d:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,11/02/2005, 4.10.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:27:26:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.106 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```
```
:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```Also, Dell's website that I downloaded the driver from said it was for a "1350 wireless adapter", why does it come up as BCM4306?

---

### Post by anewguy on 2008-08-28
That's their model number - 1350.  The chipset used is Broadcom 4306.  Once you unpack that file you downloaded you should come up with a .inf and 1 or more .sys files.  You will need those for ndisgtk.  If you have problems with that, let us know and we can walk you through ndiswrapper on it's own without the graphical interface ndisgtk.

In case you are wondering, your wireless currently isn't working under Linux as there is no driver loaded for it.  This will get your driver loaded.  There is also another method using fwcutter, but just my personal choice I prefer the Windows XP drivers and ndiswrapper (with or without the graphical front end ndisgtk).  :)

---


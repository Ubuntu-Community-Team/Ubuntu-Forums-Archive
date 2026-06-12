---
title: "wifi  isuue"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Gipsy25 on 2008-06-27
i cant connect online using wifi

my my /etc/network/interfaces shows the following ....

auto lo
iface lo inet loopback 

that is all ... wifi is on, but the 2 little pc's show a red X and also says no network connection.

if you know how to fix it please let me know ... 
thanks in advance :KS

---

### Post by MeeMaw on 2008-06-27
I think you'll get a faster response if you post this in Networking & Wireless, along with the output of   "sudo lshw -C network"  (without the quotes) 

chili555 or someone will be along to talk you through it.

:)

---

### Post by Gipsy25 on 2008-06-27
ok, i will thanks ... i appreciate it ...

---

### Post by Nxion on 2008-06-27
> **Gipsy25 said:**
> i cant connect online using wifi

my my /etc/network/interfaces shows the following ....

auto lo
iface lo inet loopback 

that is all ... wifi is on, but the 2 little pc's show a red X and also says no network connection.

if you know how to fix it please let me know ... 
thanks in advance :KS


Try this. 

Go to System >Administration > Hardware Drivers. I believe it is there.  There is what used to be called "Restricted Drivers" If its an Intel card it might need some extera packages to be downloaded. Some hardware requires restricted drivers to be installed becasue there not normaly in the normal repos.

Also have you edited the sources.list file to add exter repos, by default only most are enabled but there are a few more we can enable.

Also please post the output of these commands:

```
lspci
```and

```
iwconfig
```:)

---

### Post by Gipsy25 on 2008-06-28
ok LSPCI shows the following ... :
> 
 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
and the "IWCONFIG" shows this 
[QUOTE]
 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

[/QUOTE]

---

### Post by Nxion on 2008-06-30
Looks like you have a Broadcom card. I don't have the guide at my fingertips at this moment but I will post the guide for you when I find it. I believe there is one out there. I remember seeing on not to far back.

Also...

Did you got to "System > Administration > Hardware Drivers" ? Is your broadcom wifi card sow up in there? 

Also...

Did you edit your sources.list to add the extra repos?

Keep us posted, We want to get this working for ya!

THANKS!,
Nx

---

### Post by RequinB4 on 2008-06-30
Step by step for broadcom 43xx wireless (with double the speed of fwcutter):

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by untermensch on 2008-06-30
I use fwcutter. I could never get ndiswrapper to work. I really think my computer hates me =[.

Use either, try ndiswrapper first though. it's much better.

---

### Post by RequinB4 on 2008-06-30
> **untermensch said:**
> I use fwcutter. I could never get ndiswrapper to work. I really think my computer hates me =[.

Use either, try ndiswrapper first though. it's much better.

If you install ndiswrapper correctly, and you have an applicable card, it  should work.  The only risk is inappropriate installation, which the step by step is meant to fix.

Then again, fwcutter did NOT work on my broadcom, so I can understand.

---

### Post by untermensch on 2008-06-30
> **RequinB4 said:**
> If you install ndiswrapper correctly, and you have an applicable card, it  should work.  The only risk is inappropriate installation, which the step by step is meant to fix.

Then again, fwcutter did NOT work on my broadcom, so I can understand.

I had the opposite. I did step by step and still didn't fix my ndiswrapper. I was forced to use fwcutter because ndiswrapper didn't work.

---

### Post by Nxion on 2008-06-30
> **RequinB4 said:**
> Step by step for broadcom 43xx wireless (with double the speed of fwcutter):

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Aww, you beat me to it :). Let us know if it worked or not. :)

---


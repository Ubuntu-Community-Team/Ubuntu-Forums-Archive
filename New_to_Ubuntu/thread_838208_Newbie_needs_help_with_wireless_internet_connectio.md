---
title: "Newbie needs help with wireless internet connection"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by huntis619 on 2008-06-23
Hi all. I have a hp zv5410us laptop. When I had ubuntu 7.10 everything worked fine on my laptop. Now that I've switched to 8.04 I can't get  my wireless internet connection setup or working. Can anyone please help me.

---

### Post by z.s.tar.gz on 2008-06-23
Did you have to use ndiswrapper/etc in 7.10?
You may have the problem I did when switching to 8.

---

### Post by huntis619 on 2008-06-23
Yes I did and I was thinking about going back to 7.10

---

### Post by balagosa on 2008-06-23
do you know your WiFi card?

if not then please post the outcome of **lshw -C network**

---

### Post by z.s.tar.gz on 2008-06-23
In 7, did you have to enable the firmware from 'restricted drivers?'
If you did, you have the same problem I used to have.

Don't switch back to 7 just yet!:)

edit: btw, does your card use 43xx firmware?

---

### Post by RequinB4 on 2008-06-23
What is the output of

```

lspci

```

---

### Post by huntis619 on 2008-06-23
Sorry everyone I'm back. Here's the info   lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
steven@steven-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

steven@steven-laptop:~$

---

### Post by huntis619 on 2008-06-23
Can anyone please help me?

---

### Post by phidia on 2008-06-23
> **huntis619 said:**
> Can anyone please help me?

You have > Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Check the thread on broadcom [here]("http://ubuntuforums.org/showthread.php?t=780692&highlight=broadcom+bcm4306") and this howto [here]("http://ubuntuforums.org/showthread.php?t=779754&highlight=broadcom+bcm4306").

---

### Post by edwardLS on 2008-06-23
I have the same Broadcom BCM4306 card.  See this guide to get it working.  This worked perfectly for me.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by phidia on 2008-06-23
> **edwardLS said:**
> I have the same Broadcom BCM4306 card.  See this guide to get it working.  This worked perfectly for me.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Are you using hardy or gutsy? Just asking because the OP had wireless working until he upgraded to hardy and there seem to be known problems with some broadcom cards under hardy.

---


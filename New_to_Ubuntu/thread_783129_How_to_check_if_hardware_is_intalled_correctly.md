---
title: "How to check if hardware is intalled correctly"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Ag3nt0rang3 on 2008-05-05
Hi i am completly new to ubuntu and linux-based os. I  am having trouble setting my wireless network. I went through the troubleshooting guide and it says i need to check whether drivers are installed by going to:
System &#8594; Preferences &#8594; Hardware Information 
But i cant find 'Hardware information' anywhere. Does anyone know where i can find it?

Thanx in advance.

---

### Post by jboy012000 on 2008-05-05
Which version of Ubuntu are you using? I am using 7.10 and its in there I promise.

Although I have a laptop with a wireless connection and it does not work as it is not supported by Ubuntu yet although I am trying to find a work around for it.

Cheers

---

### Post by -random on 2008-05-05
i think this might work:

Applications > Accesories > Terminal

and type

```
lshw
```

i found this at [https://wiki.ubuntu.com/HardwareIdentification](https://wiki.ubuntu.com/HardwareIdentification) if you want to have a look at it..

---

### Post by Ag3nt0rang3 on 2008-05-05
I am using Ubuntu 8.04 LTS. Its the 64bit version if that makes a difference.

---

### Post by -random on 2008-05-05
seems you can also output the data to a nifty .html document with 

```
sudo lshw -html > your-file-name.html
```

(found at [http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/](http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/))

---

### Post by robalcorn on 2008-05-05
I am using 8.04 hardy and there is also Applications/System Tools/Sysinfo.
I can't remember if I installed it or if it was there by default.

---

### Post by game_plan on 2008-05-05
Wireless is a pain to get to work.

Please post the results of these commands so we can get you the right driver
```

lspci
lsusb

```

---

### Post by Ag3nt0rang3 on 2008-05-05
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Ag3nt0rang3 on 2008-05-05
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by kwacka on 2008-05-05
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

See the BCM4311 howto at:

[http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm4311)

---

### Post by Ag3nt0rang3 on 2008-05-05
when i try to use the terminal i get '[sudo] password for matthew:'
and i cant type my password, cant type anything in fact, all i can do is hit enter. what am i supposed to do?

---

### Post by kwacka on 2008-05-05
Try ```
sudo application
```

e.g. 'sudo gedit' 

You will then be prompted for your password, which will not be displayed. Press enter and the app will open as super-user.

---

### Post by Ag3nt0rang3 on 2008-05-05
I give up. Ubuntu Doesnt run half the programs i want it to, even with wine, and can even use wireless. I guess its back to good old xp.

---

### Post by kwacka on 2008-05-05
You may well be right.

If you have Windows applications that you require there seems to be no reason to change - this is the advantage of Windows.

I would suggest that you did not appreciate that Linux is not Windows - this is the advantage of Linux 8)

If you feel, at a future date, that you are more willing to extend your knowledge/capabilities there will be many here willing to assist you.

BTW, why not Vista?

---

### Post by Ag3nt0rang3 on 2008-05-05
Vista is probably the worst OS on the planet - slow and unstable, just pretty shite. I will try Linux at later date but at the minute it doesn't do the stuff I want it to. I really wanted to use ubuntu because it heard its a lot more stable and requires less maintenance, but I guess when you've spent all your life on Microsoft os, its kinda hard to switch. If only you could combine the stability of linux with the compatibility and ease of use of windows. O well at least I tried.

---


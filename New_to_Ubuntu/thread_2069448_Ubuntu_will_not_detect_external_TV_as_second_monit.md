---
title: "Ubuntu will not detect external TV as second monitor"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by Nyk0n on 2012-10-10
I would like to use an old TV as a second monitor and I am having some trouble with it. I have my laptop connected to my TV using an S-cable and an audio cable. My laptop is a Dell D600 with a ATI Radeon 9000 video card. I am not the best when it comes to linux commands but here is one that I am sure will help you guys in helping me solve my problem. Thanks all.

Output of lspci:

```
root@bt:~# lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```In addition, my OS is Backtrack 5 R3. This is not my main OS for those who are wondering, I use Windows XP SP3 for that. Also, my display manager is Gnome and my arch. is 32-bit.

---

### Post by Marthewicked on 2012-10-10
I know you would have posted if there are other possible connection, since the TV is old, no HDMI or VGA connections? I connect either of those on an LG TV and it is a ear plus old, hey, just an option to try.
Mar

---

### Post by Nyk0n on 2012-10-11
> **Marthewicked said:**
> I know you would have posted if there are other possible connection, since the TV is old, no HDMI or VGA connections? I connect either of those on an LG TV and it is a ear plus old, hey, just an option to try.
Mar

No. This TV just has an s-video cable input and A/V outputs

---

### Post by rrich1974 on 2013-01-04
sorry for being rude and highjack your thread. 
i have the same issue with the radeon driver. sometimes it works, sometimes dont. really drives me mad. i dnt understend why! i did not yet find a pattern to see when is working and is not. it seems randomly.  
this is my lspci:
> rich1974@rich1974-Inspiron-1521:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
 

on windows, it works perfectly. 

thanx!

---

### Post by augoldfinger on 2013-01-05
Back in my Linux experimental days (when I was trying them all for the one I liked best) I only recall "Mandrake" supporting S Video

I was ginving presentations at the time & used S Video.

Somewhere along the line, I guess around 06 I found Ubuntu Dapper Drake... Seems to me it worked great, cause I used Ubuntu until Unity :-$ ](*,)

Anyway here is an old thread, maybe it will help
[http://ubuntuforums.org/showthread.php?t=842980](http://ubuntuforums.org/showthread.php?t=842980)

---


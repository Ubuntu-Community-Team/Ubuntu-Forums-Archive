---
title: "Wireless issue"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-10-15
Hey everyone;

I just installed a lynksis router. My XP machine recognized and ask me for the pass phrase. works great (WEP key, etc) However, my Ubuntu laptop works great when connect by ethernet cable to the wireless router. However, when I disconnect, nothing. I have wireless capability enabled on the toshiba sattelite p205.... Should I not get some dialogue box poppin up saying that Ubuntu found a wirless network and ask me for the security info. Or is the wireless adapter not being recognized by Ubuntu.

I am at a loss....

Thanks

---

### Post by jbrown96 on 2008-10-15
Ubuntu (and other Distros generally) like to stay out of your way. There's no "Look at me, Look at me, Look what I found! Aren't you excited, didn't I do great" that is so typical of windows. You should be able to left-click on network-manager and it will show your wireless networks that are available. If you don't find anything listed, post back with your wireless hardware (the card in your computer), and the version of ubuntu you are using.

---

### Post by loyaleagle on 2008-10-15
Awesome.... found it.... looks a little intimidating as to what to enter, but I will figure it out....

You have been of great help.

Thanks

---

### Post by loyaleagle on 2008-10-15
However, it still does not show any wireless networks avaialable?
Only wired

---

### Post by jbrown96 on 2008-10-15
What type of Wireless card do you have? ```
lspci | grep Network
``` Is the card active? ```
iwconfig
``` see if the same wireless interface appears on the next command ```
ifconfig
``` Try to manually scan for networks (network-manager tends to interfere) ```
iwlist scan
``` Which version of Ubuntu are you using?

---

### Post by loyaleagle on 2008-10-15
lspci 

loyaleagle@loyaleagle-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
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
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
**[COLOR="Red"]17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/COLOR]**
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


loyaleagle@loyaleagle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

loyaleagle@loyaleagle-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:af:03:8a  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:feaf:38a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4708801 (4.4 MB)  TX bytes:393364 (384.1 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52607 (51.3 KB)  TX bytes:52607 (51.3 KB)

loyaleagle@loyaleagle-laptop:~$ lspci | grep Network
loyaleagle@loyaleagle-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

loyaleagle@loyaleagle-laptop:~$

---

### Post by jbrown96 on 2008-10-15
I haven't worked with Atheros wireless, so I won't be able to help you very much. Is there a driver listed in the System-->Administration-->Hardware Drivers for your card? It doesn't appear as though the system sees your card at all. Could you post the output of ```
lsmod
```

---


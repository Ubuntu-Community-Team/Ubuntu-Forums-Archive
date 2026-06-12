---
title: "need help with drivers - wireless"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by GreenFire08 on 2008-06-25
Alright, so I finally decided to go through with getting Ubuntu on my laptop, and so far it's been really great. My only issue is that I can't seem to get recognition for the driver for my wireless router. I have a linksys WRT54G router, and my laptop is a Toshiba Sattelite running on AMD Turon64x2. My wireless driver is from Atheros, and when I look for it in the terminal, it says that it's there, it just doesn't have a driver for it.

NOTE: I no longer have the setup disk for the linksys router - it was accidentally tossed during the process of moving into a new house.

Please help if at all possible and thanks!

Also, this is an awesome smiley: :guitar:

---

### Post by lswest on 2008-06-25
can you post the output of ```
lspci
lshw -C network
``` please, so we know which atheros card we're dealing with (there are a number of how-tos in the forum's tutorial section on setting up atheros cards, once we know which it is, chances are you can find your answers in one of those threads).

---

### Post by rico002 on 2008-06-25
i ahve a similar problem but mine is with dell inspiron 1525 but when i go to check the wireless networks its not there and i thnk cant configure my wirelss driver which is pretty wack...is your wireless network there can u see it on ur laptop when u check ur networks? i dunno if u could run linksys setup cd on linux maybe i should i try it, to fix mine, but the setup ip 192.168.1.1 by default and  could u post the output of this in a terminal

lspci

---

### Post by GreenFire08 on 2008-06-25
Okay then.

```
ubuntu@ubuntu:~$ lspci 
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
17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller 

```

```
ubuntu@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:11:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1b:38:45:c0:4a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:17:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 

```

Hope that helps.

---

### Post by phidia on 2008-06-25
Depending on which version of ubuntu you are using you can check out the threads [here]("http://ubuntuforums.org/showthread.php?t=766169&highlight=atheros+AR242x") , [here]("http://ubuntuforums.org/showthread.php?t=789824&highlight=atheros+AR242x"), or checkout the search results for that card [here]("http://ubuntuforums.org/search.php?searchid=43599994&pp=25").

---

### Post by GreenFire08 on 2008-06-26
Thanks for pointing me in the right direction guys - I now have internet access. :KS

---


---
title: "Need help installing Marvell Wireless Drivers"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by mike97 on 2013-09-14
I'm using a Gateway M-1617 with Lubuntu (Ubuntu 13.04). I am attempting to install this driver: [http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=DLQqS0dSp7tnJKjXJbNysH1JjbNWCwR2TLgJjdZhGJGmhQl30k2Z!-1730479504#](http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=DLQqS0dSp7tnJKjXJbNysH1JjbNWCwR2TLgJjdZhGJGmhQl30k2Z!-1730479504#)
(sry im a forum noob)

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
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
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon Xpress 1200/1250/1270]
01:05.2 Audio device: Advanced Micro Devices [AMD] nee ATI RS690 HDMI Audio [Radeon Xpress 1200 Series]
[COLOR=#ff0000]08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless (rev 03)[/COLOR]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)



```

I followed the instructions in the readme but when i use "./install.sh" I get this: ```
mike@mike-M-1617:~/Downloads/DriverInstall$ ./install.sh./install.sh: 44: ./functions: Syntax error: "(" unexpected
mike@mike-M-1617:~/Downloads/DriverInstall$ 



```

I just right click/extract here on all the zips. and open terminal in the install.sh directory, 

Also, i cant login to root, i enter the ONLY password i have created for this install and i get: ```
mike@mike-M-1617:~/Downloads/DriverInstall$ suPassword: 
su: Authentication failure
mike@mike-M-1617:~/Downloads/DriverInstall$ 



```

I've gone through 4 distro's and can't figure this out, i got close with Fuduntu but it was overheating my cpu.

---

### Post by walterorlin on 2013-09-15
All ubuntu versions use sudo and normally don't allow you to log into root. This partially is because new users can log into root as it is easy to destroy your system. The page you linked has multiple drivers which one of the ten were you trying to install.

---


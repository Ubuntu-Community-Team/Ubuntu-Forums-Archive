---
title: "Ubuntu a Bit Sluggish After Coming out of Suspend/Sleep"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by seagullplayer77 on 2008-07-15
I'm running Ubuntu Studio Hardy AMD64 on a 64-bit machine, and although I can get it into and out of suspend without any issues (haven't ever tried hibernate, though), it takes about a minute or so before it fully "wakes up." When I go to wake the machine up, I have to press Ctrl+Alt+F7 in order to get it to prompt me for my password, otherwise it'll just hang on a black screen. Not sure if that's significant or not, but I figured I would include it just in case.

Anyway, once I put in my password and my desktop comes back up, I have some functionality--I can open applications, run commands, that sort of thing--but Network Manager won't detect networks, much less connect to them. A minute or so after coming out of suspend, the screen will flicker a few times, almost like it's going into a virtual terminal, and then it'll go back to the desktop and I'll have full functionality.

This isn't a particularly horrible or dire problem, but it would be a nice thing to get fixed. It kinda sucks when you have to wait for a minute after waking your machine up before you can get an Internet connection. Any ideas?

---

### Post by phidia on 2008-07-15
Maybe include your hardware specs-including the network card. On 7.10 x86_64 (Gutsy) my network would never come back. I'm just guessing but perhaps you're using ndiswrapper or madwifi to get wireless?

---

### Post by seagullplayer77 on 2008-07-15
As you suspected, I am indeed using ndiswrapper to get my WiFi up and running. If I'm connected to a wired network, the problem with waking up is just limited to the screen flicker--I have Internet either before and after it does its little song and dance.

Anyway, here's the output of lspci:

```

chrkal@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Not sure any of that will help at all, but now it's out there.

---

### Post by seagullplayer77 on 2008-07-16
Bump

---


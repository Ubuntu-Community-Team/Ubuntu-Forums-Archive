---
title: "how to get wireless working on  the HP pavilion dv9000?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Wylkar on 2008-10-18
I have a HP pavilion dv9000 and I am unable to get the wireless card to work in Ubuntu,I assume this is because I do not have the correct driver, however I do not know how to set up a driver. It is a Broadcom card and that is about all I know.
Thanks,
Wylkar.

---

### Post by divague on 2008-10-18
In a terminal run this

$lspci

and post the output, that way we'll know the model of your card

---

### Post by Wylkar on 2008-10-18
Here's the output:


william@william-laptop:~$ lspci
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
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by divague on 2008-10-18
This how to might help you

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by bodhi.zazen on 2008-10-18
See this thread :

[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

You *may* have problems with network manager. If you do I suggest wicd :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Wylkar on 2008-10-18
Alright thanks, I will look into these.

---

### Post by Wylkar on 2008-10-18
I got the card working following the first how-to,thanks for the help.
Wylkar

---

### Post by fee33a on 2009-03-17
> **bodhi.zazen said:**
> See this thread :

[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)


I follow this URL and solved, tks.

Edit bodhi.zazen : fixed quote box.

and, you are welcome ;)

---


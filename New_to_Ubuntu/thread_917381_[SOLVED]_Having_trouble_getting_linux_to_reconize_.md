---
title: "[SOLVED] Having trouble getting linux to reconize my webcam"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-09-11
I got the Ezonics Ez-326 of newedd, because it was was on sale. when i plug it in, it is not reconized by skype, or the program cheese. I tried the EasyCam method of installing the driver, but i get this message when reloading the repositories: 

```

Failed to fetch http://blognux.free.fr/ubuntu/dists/hardy/main/binary-amd64/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

If someone could give me another way to install it, or tell me what is wrong with that repository, i would be soo grateful.

---

### Post by deathvalleyjoker on 2008-09-11
I ran lspci and then lsusb and came up with:

```

mikey@mikey-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
mikey@mikey-desktop:~$ lsusb
Bus 001 Device 005: ID 03f0:7e04 Hewlett-Packard 
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 002: ID 046d:c051 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 016: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 002 Device 013: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 0000:0000  

```

---

### Post by deathvalleyjoker on 2008-09-11
[http://ubuntuforums.org/showthread.php?p=5772050#post5772050](http://ubuntuforums.org/showthread.php?p=5772050#post5772050)


i tried harder.

---

### Post by loell on 2008-09-11
so you did it. :)

---


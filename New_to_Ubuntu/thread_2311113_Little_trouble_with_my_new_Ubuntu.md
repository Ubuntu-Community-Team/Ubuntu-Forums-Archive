---
title: "Little trouble with my new Ubuntu"
date: 2016-01-24
forum: New to Ubuntu
---

### Post by trevor29 on 2016-01-24
So, I replaced Windows Vista on an old Dell PC with the Vivid Vervet. Everything works fine except that every time I click the "Search" icon (top left in the icon bar) the screen goes bonkers. Everything else seems to work just fine. Is there a command I can use to check that portion of the GUI or is this a known problem with a fix? 

Thanks in advance for any help.

Trevor

---

### Post by sandyd on 2016-01-24
Sounds like a graphics issue, can you post the output of
```

lspci
```

NOTE:
Ubuntu Vivid will be reaching EOL in a week + a few days.
Please ensure you upgrade to the latest version (15.10) before then.

---

### Post by trevor29 on 2016-01-25
Here's the output of my lspci

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

Thanks again for your help.

---

### Post by Vladlenin5000 on 2016-01-25
It's an old machine. Your expectations regarding performance should be set accordingly. 
That said, installing the recommend proprietary nvidia driver should improve the overall performance but do not expect miracles.

---

### Post by grahammechanical on 2016-01-25
> VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)

That is what I am pointing the finger at. According to this web site the Geforce 6150LE has a maximum 256MB of shared memory. That means that this is RAM being shared with the graphic adapter to use as video memory. Personally, I would expect the Ubuntu display to go "bonkers" with 256MB dedicated memory let alone with RAM being used as video memory and a maximum of 256MB at that. 

[http://www.game-debate.com/hardware/?gid=2218&graphics=GeForce%206150%20LE](http://www.game-debate.com/hardware/?gid=2218&graphics=GeForce%206150%20LE)

This command will show if the graphic adapter is capable of running the Ubuntu Unity 3D user interface.

```
/usr/lib/nux/unity_support_test -p
```

We need to see something like this
> 
graham@sdb7-Dev:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 340.96

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

You might want to think about installing Xubuntu, Lubuntu or Ubuntu Mate on that machine instead of Ubuntu.

Regards

---


---
title: "Broadcom wireless card problems"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by SlingerXL on 2008-06-15
I have an HP Pavilion tx 1000. Here's my lspci:

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

I followed all the directions here: [http://ubuntuforums.org/showthread.php?t=769990&highlight=dv9000](http://ubuntuforums.org/showthread.php?t=769990&highlight=dv9000)

I went through all the steps. I have a fresh install so after that I went and got all the updates. Then when I STILL couldn't find any wireless networks I went and got wicd. 

Now I STILL don't get any wireless networks despite my dell inspirion (with a different wireless card) finds them fine.

What do I do now?

---

### Post by drs305 on 2008-06-15
this is the thread i used to get my broadcom 4311 (rev 1) to work in hardy. it appears very similar but not exactly the same as the thread you used. you might want to compare them to see where, if anywhere, they differ:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

---

### Post by SlingerXL on 2008-06-15
OK did it. Nothing. What the hell. I've tried like 3 different tutorials on how to get this damn card to work and it STILL won't find any wireless networks!

---

### Post by SlingerXL on 2008-06-16
Is there a special way to set up wicd to see wireless connections? I've gone through so many tutorials on how to get this card to work I wonder if it's not something else like wicd. All I've done to it was set up the wired network and I didn't know if there's a way to set up the wireless one too that I'm missing.

---


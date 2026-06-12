---
title: "Mouse disappearing when shutting laptop (HP Pavilion)"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by SlingerXL on 2008-08-30
So my mouse disappears when I close my lid most of the time. It still works to click on stuff, but it disappears. Anyone know why?

---

### Post by gmxgeek on 2008-08-30
Can you elaborate a bit more?

---

### Post by hafool on 2008-08-30
I'm new at networking and I want to start making my own network wires/cables for my office. I ordered this crimping tool from [www.lducompany.com](www.lducompany.com) (crimper should be here in a few days) and I wanted to learn if there are any other kinds of network cat5 wire crimping tools out there that would work better? [http://www.liangdianup.com/inventory/459901.htm](http://www.liangdianup.com/inventory/459901.htm) is the location for the crimp plires on thier website, those are the ones that I bought. Funny that it says Germany on the handle of the plires but I would gues they are made in China since the company I bought them from is in China. If you know of a name of a certin cat 5 wire crimper that would be better for me to use then please post it here. Thank you :)

---

### Post by gmxgeek on 2008-08-30
Please try to keep replies to posts on topic. If you wish to discuss something else, then you should make a new topic where said crimping tool may be discussed and it will be 'on topic' as opposed to here where it is 'off topic' :)

---

### Post by SlingerXL on 2008-08-31
> **gmxgeek said:**
> Can you elaborate a bit more?

What else do you need? Here's my lspci:

dan@dan-hp:~$ lspci
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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

---

### Post by SlingerXL on 2008-09-02
Any help?

---

### Post by drubin on 2008-09-02
By elaborate he meant could you please explain a little more. 

Does your mouse pointer (the little icon) disappear after you have reopened  laptop lid? But as you said you can still click but no icon on the screen.

---

### Post by SlingerXL on 2008-09-02
> **rubinboy said:**
> By elaborate he meant could you please explain a little more. 

Does your mouse pointer (the little icon) disappear after you have reopened  laptop lid?
Yes. It disappears after I open the laptop. It works like a normal mouse, I just can't see it and it's annoying. It reappears if I restart.

---

### Post by SlingerXL on 2008-09-03
No one knows what's happening?

---

### Post by proctor-the-doctor on 2009-09-14
i had this same issue on an hp tx 2000 running 9.04.

lspci shows the same entry for video:
VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)

i was able to correct this by updating the nVidia drivers from version 96 to version 180:

system | administration | hardware drivers

proctor.

---


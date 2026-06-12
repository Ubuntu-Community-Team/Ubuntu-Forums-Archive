---
title: "Computer freeze every 15 minutes"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Celosodia on 2008-11-13
I have 8.04, and my computer freezes and requires a hard reboot almost everytime I use it, usually within 15 minutes. It freezes especially when I am playing a game or watching a movie, but it is not limited to that, it will even freeze when its idle. There are no lights flashing when it happens, and the mouse and keyboard both lock. 
I am thinking it is a problem with the RAM, but I am not sure. If anybody can help me, I am willing to try anything.

---

### Post by taurus on 2008-11-13
If you think it's the RAM, you can run a memtest at the GRUB menu.  If you don't see the menu when you turn on your computer, press ESC to bring it up.  Then use the down arrow key to highlight the memtest and run it.  It could take a while though.

How much RAM (and swap space) do you have on your machine?

---

### Post by bobnutfield on 2008-11-13
This could also be a symptom of a failing graphics card.  I had a similar experience with a failing nVidia card.  It froze the computer, starting with the mouse cursor and then the entire computer.  If you have a spare card, one that you know is good, remove the current card and try it with an alternative.  If you get no freezes, then you have your answer.

While it could in fact be your memory, memory failures will not usually wait that long to start corrupting the operation, as a graphics card that is getting to higher temperature would.

---

### Post by tangibleorange on 2008-11-13
could you post the output of this command so we can look for problematic hardware:

```
lspci
```

---

### Post by Celosodia on 2008-11-13
My memory says:
Total - 470
Used - 464
Swap - 776

[HTML]:~$ lspci
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
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)[/HTML]

I really appreciate your posts and suggestions.

---

### Post by handydan918 on 2008-11-13
+1 on the memtest suggestion.

I had these sort of symptoms on a machine I built, and running memtest for a couple of hours showed nothing. 

Overnight, however, showed a bum module.

---

### Post by Celosodia on 2008-11-13
I am running a memtest right now and using a different PC. If it finds something wrong, will it automatically solve the problem or will I have to do something?

---

### Post by taurus on 2008-11-13
If the memtest comes back with a bad memory, I don't think there is anything else you can do except get a new RAM.

---

### Post by Crafty Kisses on 2008-11-13
You can also run this command when it first boots:
```
top
```
You can see how much RAM is being used.

---

### Post by Celosodia on 2008-11-13
I have been running a memtest for several hours, and no errors have shown. If nothing is found after a few more hours, I will try changing my graphics card. 

Do I have to actually change the card, or can I just update it? I have nVidia, by the way.

---

### Post by Crafty Kisses on 2008-11-13
> **Celosodia said:**
> I have been running a memtest for several hours, and no errors have shown. If nothing is found after a few more hours, I will try changing my graphics card. 

Do I have to actually change the card, or can I just update it? I have nVidia, by the way.

What do you mean by updating the card? If you mean by installing the drivers you can easily do that by going to System > Administration > Hardware Drivers and look for your NVIDIA drivers.

---

### Post by Celosodia on 2008-11-14
I have figured out the problem - it is my graphics card. It only freezes when I have desktop effects enabled; when I disabled them, it perfectly. Although, I would really like to have my desktop effects, so is there a way I can upgrade my nVidia graphics card firmware or something? Because it is on a laptop, and I don't know how to, or even if you can, change the graphics card.

---

### Post by handydan918 on 2008-11-16
> **Celosodia said:**
> I have figured out the problem - it is my graphics card. It only freezes when I have desktop effects enabled; when I disabled them, it perfectly. Although, I would really like to have my desktop effects, so is there a way I can upgrade my nVidia graphics card firmware or something? Because it is on a laptop, and I don't know how to, or even if you can, change the graphics card.

Any nvidia card made in the last 5 years should easily run compiz. Follow the previous posters recommendation for installing new drivers, and if that doesn't help, you may actually have bad hardware.

---


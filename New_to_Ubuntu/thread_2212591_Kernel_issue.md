---
title: "Kernel issue"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by zaivala on 2014-03-21
I just got a used computer, had to install hard drive and RAM. The hard drive I used was one from a computer I upgraded and the new motherboard was faulty. I had Ubuntu Karmic 64-bit on it. I upgraded, first to Lucid and then to Precise.

Now when I boot up, it goes to a blank screen (using kernel 3.2.x), but if I tell it to use an older kernel (2.6.x) it boots fine and runs great....well, sometimes a bit slow, but everything works.

What can/should I do to get the newer kernel to run?

Hardware is Dell Optiplex 740 with 3 Gb RAM (still need to buy a 4th stick or replace with 2 Gb sticks for 4 or 8 Gb). I have an off-brand monitor made by/for HP, Microsoft Natural keyboard, and Logitech Marble trackball. Video is whatever is on the motherboard, no video card.

Moss

---

### Post by su:bhatta on 2014-03-22
Well, it seems to be graphics driver problem. Find out the details of graphics card in use with :

```
lspci
```

Post the output here and maybe it will be of help.

---

### Post by Vladlenin5000 on 2014-03-22
Dell Optiplex 740 has an integrated NVIDIA Quadro NVS 210S and several ATI cards as optional. Assuming it has the integrated only it should work with older nvidia driver versions.

---

### Post by zaivala on 2014-03-22
OK, I do not understand how to use Unity. How do I get to a Terminal? I'm used to Lucid with Gnome, and Puppy... where there are icons and menus...

---

### Post by grahammechanical on 2014-03-22
On the left side of the screen is a thin panel called the Launcher. At the top of the Launcher is a Ubuntu icon. click on that and the Dash will open. In the search bar type terminal and the Dash will find it for you.

To use the newer kernel you could try selecting Recovery mode at the boot menu and then when at the Recovery menu select Resume. That will load to a desktop without activating a proprietary video driver. At the desktop use the Additional Drivers Utility to experiment with available video drivers. That may get you a working system with the latest kernels for that version of Ubuntu.

Regards.

---

### Post by zaivala on 2014-03-22
OK, now I'm having trouble cutting and psting from Terminal. Damn I'm stupid today.  I though Copy was Shift-Insert. Can't remember POaster. Ctrl-C does not work.

Silly man. My right mouse button. There ya go.

---

### Post by zaivala on 2014-03-22
zaivala@zaivala-desktop:~$ lspci
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
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)

---

### Post by zaivala on 2014-03-22
> **grahammechanical said:**
> To use the newer kernel you could try selecting Recovery mode at the boot menu and then when at the Recovery menu select Resume. That will load to a desktop without activating a proprietary video driver. At the desktop use the Additional Drivers Utility to experiment with available video drivers. That may get you a working system with the latest kernels for that version of Ubuntu.

This worked.  So now I just need help with what to configure to get the right video driver loaded. THanks everyone.

---

### Post by zaivala on 2014-03-22
And to show I'm not a total idiot, I went and downloaded the latest full Nvidia drivers, and it works fine. Looks a bit sharper even. Thank you all.

---


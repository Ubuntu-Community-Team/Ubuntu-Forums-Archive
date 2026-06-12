---
title: "Sound and Graphics Problems"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Haioko on 2008-07-29
Whenever I try to play a fullscreen game (Like WoW on Wine or Alien Arena (Which I downloaded from Synaptic)) The graphics go all wonky and change colour. It basically goes back to like 16 bit res. And I have to restart my system to get it back to normal.

Also I'm having problems with my sound. Files will play but no sound comes out of my speakers. The speakers work fine as I've tested them on another computer. :confused:

---

### Post by halitech on 2008-07-29
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 95c5
05:00.1 Audio device: ATI Technologies Inc Unknown device aa28

```

I know this is your lspci info

do you have an ATI card in this machine for a video card or do you know?

---

### Post by Haioko on 2008-07-29
Yeah it's a radeon EAH3450

---

### Post by halitech on 2008-07-29
and under restricted drivers there is no drivers listed that you can use?

your video problem is due to not having the correct video card drivers installed although how its linking to an audio device makes no sense to me

---

### Post by Haioko on 2008-07-29
Where is restricted drivers?

---

### Post by halitech on 2008-07-29
if you are using 7.10 its under System - Administration - Restricted Drivers Manager

if you are using 8.04 its under System - Administration - Hardware Drivers (I think)

---

### Post by Haioko on 2008-07-29
It's 7.10.

I clicked on it but it comes up 'Your hardware does not need any restricted drivers'

---

### Post by halitech on 2008-07-29
ok, so it doesnt detect the video card as being something that it has drivers for

I wonder if you open a terminal and do
```
sudo apt-get install xorg-driver-fglrx
```
if that will help by installing the ati video drivers

---

### Post by Haioko on 2008-07-29
Got this:

scott@scott-desktop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for scott:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
xorg-driver-fglrx set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---


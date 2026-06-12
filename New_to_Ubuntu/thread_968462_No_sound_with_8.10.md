---
title: "No sound with 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Smittysmit on 2008-11-02
I just installed 8.10 (386) on a desktop.  I am unable to get any sound.  I am using the SP/DIF connector on the MOBO to feed an audio receiver.   On earlier versions of Ubuntu, I would just need to install ALSA-GUI then enable the digital (IEC958 (or something like that)).  I just installed ALSA-GUI but there are only 2 options (Master & Capture).  At the top it says the card/chip is "Pulse Audio".

I tried installing the GNOME ALSA Mixer which has more options but still no audio.

Any thoughts?

---

### Post by Crafty Kisses on 2008-11-02
What are the results of this command?
```
lspci
```

---

### Post by Smittysmit on 2008-11-02
smitty@smitty-desktop:~$ lspci
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
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation NV42 [GeForce 6800 XT] (rev a2)
04:07.0 Multimedia audio controller: Creative Labs SB X-Fi
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
smitty@smitty-desktop:~$

---

### Post by gdi2k on 2008-11-14
I have the same issue. Did you have any luck fixing it? 

In my case I normally have to enable the IEC958 checkbox in the settings, but this doesn't seem to work like it did in 8.04.

---

### Post by Smittysmit on 2008-11-14
I went back to 8.04...for now.

---

### Post by Eisenwinter on 2008-11-14
You could try to install the ALSA drivers from source.
After you unpack the tarballs, use ./configure --with-cards=emu20k1, then make, and sudo make install.

You'll have to install alsa-driver, alsa-lib, and alsa-firmware.

alsa-utils is optional, but recommended, so you can access the alsa mixer through alsamixer in terminal.

---


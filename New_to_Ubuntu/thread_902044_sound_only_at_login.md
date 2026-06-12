---
title: "sound only at login"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-08-26
i have been running ubuntu for 2 weeks and in between did something stupid by running one of the installation scripts in these forums to install alsa 1.0.17 instead of the existing 1.0.16. After i did that i have lost my sound
i get only the login sound. When i try testing the sound in the preferences by setting it to ALSA i get this:

 audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

Kindly help me fix this, i tried reinstalling alsa by removing the existing one bu that didnt work

---

### Post by nicedude on 2008-08-26
try this

sudo alsamixer

and see if the volume is turned up or not, if not turn it up.

In general when you install from source it is good to keep the source so you can uninstall from source if necessary :-)

---

### Post by siddharthshukla on 2008-08-27
i maxed the volume in all the channels in alsamixer still i get no sound, i installed alsa thru apt-get so not sure if the source is present or not. Also this is the output of lspci:

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
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

and the output of aplay -l is:*

*** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---


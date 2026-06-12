---
title: "No Sound Card Found"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by OneEarWillie on 2012-01-06
I am brand new to Linux and Ubuntu... this is my first post.

I recently discovered Linux and immediately began installing Ubuntu  11.10 on every PC I had (replacing all of my pirated copies of Windows 7).  Ahh... feels nice...  **deep relaxing breath**

Here's my current dilemma:

On my main system, I cannot get sound to work.  The Mainboard has built in sound ports... and on boot up it produces the standard BIST beeps and stuff (via those ports).  But once Ubuntu is booted... no sound.  On other systems I have no trouble with sound... I get the Ubuntu login sound, and movies have sound... no configuration needed.  But this system... nuthin'. :confused:

I searched around a bit and tried the following:

**aplay -l**
aplay: device_list:240: no soundcards found...

**modinfo soundcore**
filename:       /lib/modules/3.0.0-14-generic/kernel/sound/soundcore.ko
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     8C2CC496EFFF806BFEE1D0C
depends:        
vermagic:       3.0.0-14-generic SMP mod_unload modversions

**lspci**
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev b1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [Quadro FX 1500] (rev a1)
80:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
80:01.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev b1)
80:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
80:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
80:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
80:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
80:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)

From the looks of things... I would guess that I have no sound controller or that perhaps it is not enabled in the BIOS.  However, I've poked around in the CMOS menus and I can't find any thing about enable/disable onboard sound.

Does anybody know what I'm doing... 'cause I sure don't?

Thanks for your assistance,
OEW

---

### Post by Basher101 on 2012-01-06
piracy is bad, glad you are away from it.

are you even using your sound card? check your settings

---

### Post by OneEarWillie on 2012-01-06
Yes, piracy had been a normal part of my life for many years... it feels nice to be legal for a change.

When I go to **System Settings->Sound** under the *Hardware* tab... I have no devices listed.  Under the *Output* tab I only have *Dummy Output*.

---


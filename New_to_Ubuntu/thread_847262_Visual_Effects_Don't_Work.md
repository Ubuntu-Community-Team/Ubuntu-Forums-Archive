---
title: "Visual Effects Don't Work"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-07-02
Whenever I go to change the visual effects on my computer from None to Normal, I get this error message that says "Visual Effects Could Not Be Enabled"... Any Ideas on how to fix this???

---

### Post by S1xp4ck on 2008-07-02
Check  System/Administration/Hardware Drivers and assure you have the necessary drivers installed for your card.  Compiz depends on Nvidia or ATI proprietary drivers for effects to work.

---

### Post by Johnathannn on 2008-07-02
Alright, I checked that, and all I have there is a "Broadcom B43 Wireless Driver" that is enabled... What does that mean:lolflag:?

---

### Post by S1xp4ck on 2008-07-02
It means you have no driver installed for your video card or you have a card that may not support the video acceleration needed to run desktop effects.


Do you happen to know the make of your video card?

---

### Post by Xerp on 2008-07-02
You don't always need a restricted driver. Intel cards, for example :)

Run ```
lspci
``` and paste the output.

---

### Post by Johnathannn on 2008-07-02
Is there anyway I can check that using the terminal or...something? I'M PRETTY SURE that I have an SIS Video Card...I have an Acer Aspire 5000 Laptop... But that's all  I know... Thanks!

---

### Post by rxtx on 2008-07-02
```
sudo apt-get install sysinfo
```

I found this quite a handy little GUI util. Should be able to find your chipset in there somewhere- it may not support hardware accelerated rendering :(

---

### Post by Johnathannn on 2008-07-02
Ok, just saw your post Xerp, ran that command in the terminal, and got this...

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by S1xp4ck on 2008-07-02
> **Xerp said:**
> You don't always need a restricted driver. Intel cards, for example :)

If he is on the Acer laptop in his signature it is most likely a SIS brand card (prolly a Mirage 2).  I am not sure if that card will support Compiz

---

### Post by Xerp on 2008-07-02
Yup, there is the video chip:

VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

So it looks like no compiz support :(

---

### Post by Johnathannn on 2008-07-02
So, I can't have visual effects at all? lol that sucks big time... Nothing I can install or anything eh? Alright, thanks so much guys!

---


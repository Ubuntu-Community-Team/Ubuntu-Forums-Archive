---
title: "No Sound New Install"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by HookMan on 2008-06-28
Okay.... I am a new open source user. I have installed ubuntu and the problem is I have no sound...... Help !!!

HookMan

---

### Post by jakupl on 2008-06-28
goto Accessories --> terminal

can you post the output of

```
lspci
```

---

### Post by HookMan on 2008-06-28
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0f.0 Multimedia video controller: Sony Corporation Unknown device 8087 (rev 01)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

---

### Post by HookMan on 2008-06-28
Hope you are still here.... Help ....

---

### Post by iaculallad on 2008-06-28
To to use ALSA for your sound card driver:

Navigate to System->Preferences->Sound, under the "Devices" tab, change the settings of "Sound Events", "Music and Movies", from "AutoDetect" to "ALSA-Advanced Linux Sound Architecture". Click on close button and retry using your sound card.

---

### Post by HookMan on 2008-06-28
Okay I can hear a cd play..... but no system sounds or any video ..... ABC news etc with flash player installed. I am listening through a USB headset / Mic

I did not use "ALSA-Advanced Linux Sound Architecture". I used USB audio ... only one that worked with the test button.

HookMan

---

### Post by iaculallad on 2008-06-28
Install the audio support wrapper for non-free flash plugin then retest your sound:


```
sudo apt-get install libflashsupport
```

---

### Post by HookMan on 2008-06-28
I instaleed your recommendation but I cannot hear a flash video.....

---


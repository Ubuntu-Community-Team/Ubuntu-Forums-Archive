---
title: "No sound at all"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Tsula on 2008-05-26
I'm having this problem where when the system boots up, if the opening theme doesn't play, there will be no sounds throughout the whole session. If there is, then the sound will be fine. What's the issue here? And it happens where there is no sound more often than there is...I have no soundcard, it's all onboard.

---

### Post by Tsula on 2008-05-30
*bump* 

The comprehensive sound guide was of no help either...

---

### Post by diablo75 on 2008-05-30
A few questions:

What version of Ubuntu are you running?  
Is this a fresh install, or an upgrade from a previous version?  
How long has the problem persisted?  
When you say startup sound, do you mean the bongo's at the login screen or after login?  
Do you have more than one sound card (perhaps on-board sound plus an additional card in a PCI slot)?

---

### Post by lisati on 2008-05-30
> **Tsula said:**
> I'm having this problem where when the system boots up, if the opening theme doesn't play, there will be no sounds throughout the whole session. If there is, then the sound will be fine. What's the issue here? And it happens where there is no sound more often than there is...I have no soundcard, it's all onboard.

> **diablo75 said:**
> A few questions:

What version of Ubuntu are you running?  
Is this a fresh install, or an upgrade from a previous version?  
How long has the problem persisted?  
When you say startup sound, do you mean the bongo's at the login screen or after login?  
Do you have more than one sound card (perhaps on-board sound plus an additional card in a PCI slot)?

Additonal question: What sort of system are you using?

---

### Post by Tsula on 2008-05-30
Hmmm...okay...here goes.

I'm running Hardy. It was a fresh install, no upgrade. I've always had the problem. When I say sound, I mean all sound, including the sound at the splash screen (login screen). I have no other soundcard in the computer.

And what do you mean by what sort of system? Here's the result for lspci:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by lisati on 2008-05-30
My eperience of getting sound to work was with 7.04.

You might like to look here: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Tsula on 2008-05-30
I've already tried that.

---

### Post by marufaberlin on 2008-05-30
does it work (partly) after
```

killall pulseaudio

```?

---

### Post by Tsula on 2008-05-30
killall pulseaudio didn't do anything.

---

### Post by marufaberlin on 2008-05-30
ok. just an idea, sorry. it works for me.

---

### Post by Tsula on 2008-06-04
Anything yet? >.>

---

### Post by Tsula on 2008-06-05
*waits*

---


---
title: "Audio 'Crackles' on Laptop Ubuntu 8,04"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by wetinwales on 2008-09-02
Installed Ubuntu *.04 on HiGrade R5400,
Audio has a 'crackle' in right hand speaker. OK in left - regardless of volume settings and independant of the actual sound.
was OK in MS WinXP (which has been joyfully expunged forever)
Can anyone suggest what may be happening and a cure?

Thanks

---

### Post by canthus13 on 2008-09-02
The first thing I would do is verify that it isn't a physical problem.  I know you said that it worked fine in XP, but it is still quite possible that something happened to loosen a wire.  Does this also happen with headphones?

--Me

---

### Post by wolfen69 on 2008-09-02
post the output of ```
lspci
```so we know what kind of soundcard you have.

---

### Post by wetinwales on 2008-09-05
Hi there

Yes it is the same at the sound output socket (phones or PA etc) and it is the same regardless of volume settings - either physical volume knob or virtual slider in Ubuntu top panel:confused:

---

### Post by wetinwales on 2008-09-05
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 70)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 70)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Sorry I am slow. This is laptop lspci for Audio 'Crackle'

Thanks

---

### Post by canthus13 on 2008-09-05
Here's a thread with a few ideas that might help.  The info is kinda outdated , but may still have some info for you.

[http://ubuntuforums.org/showthread.php?t=128053]("http://ubuntuforums.org/showthread.php?t=128053")

--Me

---


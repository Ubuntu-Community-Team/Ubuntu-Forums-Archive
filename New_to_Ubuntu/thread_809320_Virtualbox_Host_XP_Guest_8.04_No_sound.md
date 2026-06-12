---
title: "Virtualbox Host: XP Guest 8.04 No sound"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Miller12 on 2008-05-27
Can someone please tell me how to get sound when running Ubuntu 8.04 as a guest OS in VirtualBox with XP as the host. In the VirtualBox GUI I have sound enabled with 
Host Audio Driver: Null Audio Driver
Audio Controller: ICH AC97
Guest Additions have been installed. Volume is all the way up with the Intel 82801AA-ICH (Alsa mixer) in the panel applet, but I still don't have any sound.

lspci gives:
```
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
```

I forgot to mention it is VirtualBox 1.6.0

---

### Post by LeoSolaris on 2008-05-27
Try using PulseAudio from the drop down menu rather than the Null Audio Driver. That's the only thing different that I do, and my sound works.

If that doesn't work, hopefully someone else knows a few different tricks to try.
Leo

---

### Post by byStanderone on 2009-03-18
leoSolaris...you are right, thanks for the info.

---

### Post by gigo6000 on 2009-09-14
Using PulseAudio worked for me thanks a lot

---

### Post by iosef86 on 2010-04-07
What if PulseAudio isn't an option? I have the same problem, but my only two options are the Null Audio and Windows DirectSound, It's set to Windows DirectSound but there's still no sound, any ideas would be greatly appreciated! Thanks!

---

### Post by Chronon on 2010-04-07
You have the opposite scenario (XP host, Ubuntu guest).  You're probably better off waiting for advice in your own topic.

---


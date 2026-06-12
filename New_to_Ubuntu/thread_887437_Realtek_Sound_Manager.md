---
title: "Realtek Sound Manager"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Diya on 2008-08-12
Hi!
I used to have a program called "Realtek Sound Manager" on my Windows XP. 

It was capable of controlling *any* sound that's played. For example, adding Generic or Bathroom reverb to whatever sound that is played (Even system sounds). It can also sense if I plugged/unplugged headphones, a mic, etc.

Guess it's a driver software? Anyway, I visited Realtek.com, downloaded the latest driver update, and installed it. I ended up re-installing Ubuntu as it corrupted my system.

Here is lspci if that would help:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

Is there anyway I can have it on Ubuntu? (Btw, I uninstall Windows OS, and now Ubuntu 8.04 Hardy Heron is my main & only OS) :)

---

### Post by kpkeerthi on 2008-08-12
Not quite. I guess the closest you can get in ubuntu is alsamixer.

Open a terminal and type **alsamixer**. 

:)

---

### Post by kostkon on 2008-08-12
> **kpkeerthi said:**
> Not quite. I guess the closest you can get in ubuntu is alsamixer.

Open a terminal and type **alsamixer**. 

:)
No the closest in Ubuntu is PulseAudio. It can do with audio the above and many other things.

It is the default in Ubuntu 8.04.

If you use 8.04 then follow this how-to in order to setup your system to fully utilise PulseAudio and have a variety of effects:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by nicedude on 2008-08-12
You could always just buy generic speakers or put speakers in your bathroom and listen to the bathroom reverb that way :-)

Sorry to be such a smarty pants but bathroom reverb struck a funnybone and I have been up for way too long :-) .

But seriously just use the alsamixer program to control all your inputs and outputs since it has a GUI and is pretty simple & straitfoward. Realtek makes those type of system tray programs to go along with their windows drivers and I am pretty sure they won't be coding them for Linux anytime soon. Good news is that they are not needed to get excellent sound and video playback with all media formats I am aware of. If you can listen to it or watch it in Windows then you can do the same in Linux. Minus some DRM protected files of course, but who wants those?

My 2 cents

---

### Post by Diya on 2008-08-12
> **nicedude said:**
> You could always just buy generic speakers or put speakers in your bathroom and listen to the bathroom reverb that way

No kidding! Looks like this is really the only way afterall!! :lolflag:

I've tried both Alsamixer, and PulseAudio. All they can do is adjust the master volume, Stereo, mic etc. but that's all, they don't add effects such as reverb.

I really miss my windows now..

---


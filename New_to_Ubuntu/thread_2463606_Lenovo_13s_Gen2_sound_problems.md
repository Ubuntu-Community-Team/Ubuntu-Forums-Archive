---
title: "Lenovo 13s Gen2 sound problems"
date: 2021-06-14
forum: New to Ubuntu
---

### Post by perpetuallyconfused on 2021-06-14
I'm not new to ubuntu but it has been a long time since I installed it on a new laptop and had to troubleshoot problems so i may as well be new.

Laptop = Lenovo 13s Gen 2
Ubuntu 20.04.2 LTS
Issue = Sounds plays fine on Windows. On ubuntu there is no sound from the internal speakers. If I plug in wired headphone it just gives a screeching sound whether or not sound is playing. If I use HDMI to connect to a tv the sound plays just fine. If I connect to bluetooth headphones the sound plays just fine.

Alsa info [HTML]http://alsa-project.org/db/?f=54a6f2b6c7c266bf17e98fbc09658113eb33d4c1[/HTML] seems to indicate codec is Realtek ALC287. If i read this bug report [HTML]https://bugzilla.kernel.org/show_bug.cgi?id=208555[/HTML] right it seems I'm out of luck and there is no solution at this time?

Although on [HTML]https://psref.lenovo.com/syspool/Sys/PDF/ThinkBook/ThinkBook_13s_G2_ITL/ThinkBook_13s_G2_ITL_Spec.PDF[/HTML] it said Realteck ALC3306 is the codec.

lscpi output is below```

00:00.0 Host bridge: Intel Corporation Device 9a14 (rev 01)
00:02.0 VGA compatible controller: Intel Corporation Device 9a49 (rev 01)
00:04.0 Signal processing controller: Intel Corporation Device 9a03 (rev 01)
00:06.0 PCI bridge: Intel Corporation Device 9a09 (rev 01)
00:07.0 PCI bridge: Intel Corporation Device 9a27 (rev 01)
00:08.0 System peripheral: Intel Corporation Device 9a11 (rev 01)
00:0d.0 USB controller: Intel Corporation Device 9a13 (rev 01)
00:0d.3 USB controller: Intel Corporation Device 9a1d (rev 01)
00:14.0 USB controller: Intel Corporation Device a0ed (rev 20)
00:14.2 RAM memory: Intel Corporation Device a0ef (rev 20)
00:14.3 Network controller: Intel Corporation Device a0f0 (rev 20)
00:15.0 Serial bus controller [0c80]: Intel Corporation Device a0e8 (rev 20)
00:16.0 Communication controller: Intel Corporation Device a0e0 (rev 20)
00:1f.0 ISA bridge: Intel Corporation Device a082 (rev 20)
00:1f.3 Multimedia audio controller: Intel Corporation Device a0c8 (rev 20)
00:1f.4 SMBus: Intel Corporation Device a0a3 (rev 20)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a0a4 (rev 20)
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a809
```

Any insights into how I may be able to get wired headphones or the internal speakers to play would be appreciated.

---


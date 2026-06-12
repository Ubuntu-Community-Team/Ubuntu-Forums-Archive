---
title: "Lost all my sound in Ubuntu 8.04"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by malefestra on 2008-10-04
Here's my output of lspci:

> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:04.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:04.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
01:09.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)


I installed 8.04 awhile ago.  Had no problem with sound.  Then, after a game of hedgewars today, it went out.  I've browsed the forum a little bit, have tried switching from autodetect to ALSA in the System->Prefs->Sound, but nothing.

---

### Post by Mud.Knee.Havoc on 2008-10-04
If it happened after playing a game, it's probably not a permanent change.  Does it persist after a reboot or logging out?

---

### Post by malefestra on 2008-10-04
MKH,

Yes -- it has stayed the same though both a reboot and a logout/login.

---

### Post by Mud.Knee.Havoc on 2008-10-04
This may sound obvious, but just in case... have you tried doublechecking your mixer settings to make sure it's not muted?

---

### Post by malefestra on 2008-10-04
MKH - 

No offense taken.  I did check that.

---

### Post by kansasnoob on 2008-10-04
There are some persistent problems with Pulse Audio in 8.04. This tutorial solved it for me:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

NOTE: there are i386 and 64 bit specific steps!

I followed that by installing Flash 10 Beta, but that may not be necessary!

If it is look here:

[http://ubuntuforums.org/showthread.php?t=906896](http://ubuntuforums.org/showthread.php?t=906896)

---

### Post by malefestra on 2008-10-05
Followed that tutorial.  Still no fix.  It's been intermittent -- i.e. I'll have sound for awhile, it'll cut off (sometimes mid-youtube video) and then I won't have it for awhile, then it'll be back.

Any other ideas?

---


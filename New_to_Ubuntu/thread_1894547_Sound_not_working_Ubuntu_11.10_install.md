---
title: "Sound not working Ubuntu 11.10 install"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by llbeeman on 2011-12-12
New to Ubuntu, but always heard great things about Linux so I took the plunge.  However, audio is not working at all.  I've tried to hunt down all the potential volume sliders from Systems Settings to keyboard locks to individual programs.  Windows XP Hardware Manager says I'm using Realtek High Definition Audio driver.  The only output device available in System Settings is "Internal Audio Analog Stereo." Ubuntu lspci output is:


00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Please help me....I'm lost.

---

### Post by sandyd on 2011-12-12
> **llbeeman said:**
> New to Ubuntu, but always heard great things about Linux so I took the plunge.  However, audio is not working at all.  I've tried to hunt down all the potential volume sliders from Systems Settings to keyboard locks to individual programs.  Windows XP Hardware Manager says I'm using Realtek High Definition Audio driver.  The only output device available in System Settings is "Internal Audio Analog Stereo." Ubuntu lspci output is:


00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Please help me....I'm lost.
Have you tried [http://ubuntuforums.org/showpost.php?p=9383311&postcount=30](http://ubuntuforums.org/showpost.php?p=9383311&postcount=30) ?

---

### Post by llbeeman on 2011-12-15
Sorry, that didn't work.  After much searching on the interwebs, I found this and it worked.  Don't know why.

Open file:
sudo nano /etc/modprobe.d/alsa-base.conf

Add this to the bottom:
options snd-hda-codec-realtek index=-2

Reboot

---

### Post by Ms. Daisy on 2011-12-15
Glad you found a solution.
If your problem is solved, please mark your thread as "solved" by clicking on "thread tools"

---


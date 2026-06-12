---
title: "[SOLVED] Sound problem"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-06
Hi all,

  i have ubuntu hardy heron in my box. No dual boot only linux ubuntu. I can hear sounds from websites that play videos or games etc **but even that too are very feeble**. But i cannot hear sounds from music file that are in local. even the default sample file like "ubuntusax.ogg" etc and i cant play music files from audio or mp3 cd. i installed "Gstreamer video as well as mp3 codecs" from Add/remove apps. Even after that i cannot hear any sounds (i feel but the vlc player plays the file since seek bar in player moves to count down or up) but no sound. what i have to do please help  me.

  Also am posting the o/p of "lspci"

```

gopal@gopal-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
**00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)**
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by joshsmith on 2008-07-06
probably you have trouble with pulseaudio

installing the package libflashsupport may be the magic fix

---

### Post by mailtwogopal on 2008-07-06
hi jo,

  i tried with alsamixer and my cd music is playing and am hearing sounds fine, but i have noticed whenever i put my mp3 or audio cd in drive and when it automatically opens it is showing files with extension .wav only and not mp3 or something it is actually. Why is this so? will it makes any difference in it. please clarify. also i try the libflashsupport.

---


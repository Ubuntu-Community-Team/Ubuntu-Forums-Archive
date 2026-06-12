---
title: "my sound is not working"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by iyaduncc on 2008-11-18
can i get some help with sound problem...cant hear anything...i have ubuntu 8.10....

---

### Post by jpoRS on 2008-11-18
Double click the speaker icon in the panel.  Go to preferences and select EVERYTHING.  Close out, then look at your volume controls, is anything muted?  If so unmute it and let us know what happens.

jim

---

### Post by iyaduncc on 2008-11-18
everything is checked, unmuted, still have no sound....thanks for your help

---

### Post by jpoRS on 2008-11-18
What are you working with for hardware?  The more information you give people the easier it is for them to help you.

jim

---

### Post by iyaduncc on 2008-11-18
the results of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

i am not sure what info u need... am still a begginer...sorry

---

### Post by iyaduncc on 2008-11-18
results of alsamixer :

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Realtek ALC268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;                        &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100   100<>100  100<>100 100<>100 100<>100  100<>100                     &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Mic Boos  IEC958  IEC958 D   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

### Post by jpoRS on 2008-11-18
Being a beginner isn't a problem, it is just difficult to help when you don't know the question.  Helpful tip:Give any information that you suspect might be even remotely relevant.  What may look unremarkable to you may be the key to the puzzle for someone else.

ANYWAY! The problem at hand . . . System>Preference>Sounds  What do you have everything set to?  Do any of the test buttons give you any sound?

jim

---

### Post by iyaduncc on 2008-11-18
thnks for ur help...evrything is set to alsa advanced linux sound architecture....when testing, i cant hear nothing.....i tried changing from alsa to another but still same results

---

### Post by Trafferth on 2008-11-18
Hello iyaduncc,

Two things you might want to try:

1. Right-click on the volume control and try selecting a different device to play back.  I have an Audigy sound card, for example, and yet there are still five options listed in this list only 'Audigy 1 [SB0090] (Alsa mixer)' being the right one.  Perhaps it is simply a matter of the wrong device being selected here.

2. If that doesn't work, open the volume control with a double-click, and look for a 'Switches' tab or similar - the mixer might be trying to send out a digital signal, and you are plugged into analogue, or vice versa.

Let us know how you get on!

Good luck!

Trafferth :)

---

### Post by jpoRS on 2008-11-18
Try setting them to auto detect and/or PulseAudio . . . anything?

If that doesn't work, try Trafferth's suggestions, expecially the second one.

jim

---

### Post by iyaduncc on 2008-11-18
in the switches tab i have 4 choices and they are all ticked
IEC958
IEC958 default PCM
caller ID
off-hook

---

### Post by iyaduncc on 2008-11-18
sorry but nothing is changed

---

### Post by Trafferth on 2008-11-18
Did you try the right-click > preferences option (changing the playback devices?)

-T

---

### Post by iyaduncc on 2008-11-18
yes...unfortunatley nothing

---

### Post by mr-Kirch on 2008-11-18
that happened to me, i just switched back to 8.04 because i still had my disk that i got in the mail. everything works flawlessly for me on 8.04 im just going to wait until a new lts comes out just to be safe

---

### Post by Trafferth on 2008-11-18
Hmm...

Okay, here's one more suggestion (grasping at straws here!): try plugging in a pair of headphones into the headphone socket (it's usually the green one), and see if any sound is coming out from that.  It would be useful to know if anything is coming out of your sound card at all.

-T

---

### Post by iyaduncc on 2008-11-18
i cant hear anything using headphones

---

### Post by Trafferth on 2008-11-18
One of the guys in this forum solved his problems using alsamixergui.  Might be worth a shot.  Get it using apt-get:

```
sudo apt-get install alsamixergui

```

Then run it:

```
alsamixergui

```

And unmute everything.  The reason I mention this is because the other guy found that alsamixergui worked independently of the settings in the volume control.  While I can't quite see how that works, it's worth a try.

- T

---

### Post by iyaduncc on 2008-11-18
mmm still cant hear nothing :(

---

### Post by Trafferth on 2008-11-18
Kay, I think I'm out of my own ideas. :lolflag:

Have you tried the how-to at:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=restart+pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=restart+pulseaudio)

Worth a shot.

- T

---

### Post by iyaduncc on 2008-11-18
thanks

---


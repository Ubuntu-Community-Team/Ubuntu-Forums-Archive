---
title: "Audio on Acer Aspire 5100"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by deathbymetal on 2008-10-31
I just installed 8.10 on my Acer Aspire 5100 and no sound comes out of my speakers just a crackling noise, I have tried other solutions for other peoples problems i found on a search, including changing from ALSA to OSS and back again. If it helps here is my lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by Ubuntiac on 2008-10-31
One guess here...

Your soundcard seems to be ATI which implies that it's bundled on your videocard. Given this I'm guessing that you probably need ATI's fglrx driver installed. The latest beta version can be installed by the package envyng-qt if you're on kubuntu, or envyng-gtk if you're on Ubuntu.

To install these just open up Adept Manager / Synaptic, search for the appropriate package from above and choose install. After that, run it from the menu or command line and click the "Enable" checkbox next to the "Recommended" driver. Click apply and wait for the magic to finish.

Hope this helps!

---

### Post by deathbymetal on 2008-11-01
Thanks for the reply, I installed envyng-gtk and still no audio.

---

### Post by roger_1960 on 2008-11-01
Hi

If you run

alsamixer

in terminal, are your master ad PCspeaker volumes set above zero?

---

### Post by deathbymetal on 2008-11-01
My master volume is at 100, there isn't a pc speaker volume control there. Just to be clear I dont hear any of the actual intended sound, just a crackling noise whenever i should hear a sound. Using headphones provides the same result. 

Thanks

---

### Post by roger_1960 on 2008-11-01
Hi

The PC speaker vol control is at the far right - use the left right arrows to scroll.  I did have this problem once with my aspire 5101 (in 8.04) so its worth checking.

---

### Post by deathbymetal on 2008-11-01
Thanks dude, I didn't have the pc speaker turned up, I can't believe I didn't think about checking that.

---

### Post by klaasvanschelven on 2009-05-01
> **Ubuntiac said:**
> One guess here...

Your soundcard seems to be ATI which implies that it's bundled on your videocard. Given this I'm guessing that you probably need ATI's fglrx driver installed. The latest beta version can be installed by the package envyng-qt if you're on kubuntu, or envyng-gtk if you're on Ubuntu.

To install these just open up Adept Manager / Synaptic, search for the appropriate package from above and choose install. After that, run it from the menu or command line and click the "Enable" checkbox next to the "Recommended" driver. Click apply and wait for the magic to finish.

Hope this helps!

On my Acer Aspire 5100 this hosed my videodriver to the point of not being able to start Ubuntu at all. Uninstalling gives me a workable Ubuntu, but with non-optimal video driver. No hard feelings, but at least I'd like to leave a relevant remark for other Acer Aspire 5100 users who might feel like trying the above.

---


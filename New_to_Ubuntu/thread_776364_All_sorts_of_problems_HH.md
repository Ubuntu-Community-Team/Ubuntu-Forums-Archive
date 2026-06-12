---
title: "All sorts of problems HH"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Tomsolomon on 2008-04-30
Ive installed Hardy on my L30-134 PSL-33e Toshiba. I'm having all sorts of problems. Audio, Graphics, video playback, hung aps, you name it I'm getting it. Have I got the right version installed or is HH just not compatible with this laptop? Please I realy like the idea of not having to rely on Window and I would like a working version of Linux.....
I've installed the latest x86 distro, should I have installed the 64bit.

---

### Post by dangerpl on 2008-04-30
How much RAM do you have? I have the same sound card as you and sound works perfectly on my laptop(also a Toshiba). Don't install the 64-bit because you have a 32-bit processor.

---

### Post by Tomsolomon on 2008-04-30
There's 512Mb of ram but I don't believe the problems are related to the ram.
Perhapse the installation is corrupt or something.I don't know.

---

### Post by dangerpl on 2008-04-30
Did you try reinstalling? Also, do you have all the Gstreamer codecs installed?

---

### Post by Tomsolomon on 2008-04-30
Its a clean install fully updated and Gstream codecs are installed.
Is there any sort of out put file I can bring up like an error log file or similar?

---

### Post by dangerpl on 2008-04-30
How about flash-plugin-nonfree? Do you have that installed?

---

### Post by cubeist on 2008-04-30
log files are at system/admin/system log (or /var/log from a terminal)

Did you try lspci from a terminal to see if most of your hardware is correctly recognized.

Also, what are the specific problems with audio, video, etc..

---

### Post by Tomsolomon on 2008-04-30
When you say Flash plugin do you mean Browser plugins.
Here is a list:-

Default Plugin
Demo Print Plugin
DivX Web Player
Helix DNA Plugin: Realplayer G2
ITunes Applicator Detector
Quicktime Plugin 7.2.0
Shockwave Flash
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin (compatible Totem)
Windows Media Player Plugin 10 (compatible Totem)

---

### Post by Tomsolomon on 2008-04-30
Here is the lspci output:-

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

And the Sys log is very very large.... Would probably fill a page or two on here.

---

### Post by Tomsolomon on 2008-04-30
Also there is no out for headphones in alsa.

---

### Post by cubeist on 2008-04-30
> **Tomsolomon said:**
> Here is the lspci output:-

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

And the Sys log is very very large.... Would probably fill a page or two on here.

It looks like your system is recognizing the key components of your system... what *exactly* do you have questions about...
to say that nothing is working, audio, video, etc, is just too generic for us to help you!

---

### Post by Tomsolomon on 2008-05-05
Ok I'm getting somewhere, but very slowly.
Ive been messing with /etc/modprobe.d/alsa-base, 
The speakers are now working, also the headphone switch is working, but I still don't have any audio from the headphones.
Ive got a USB audio device which works (drums on insertion) but no audio output, and it does not switch the main speakers of.

I have video working now, ATI drivers and Catalyst Control Center are installed and working, but still having problems with artifacts in the display, especially on boot and shut down.

---

### Post by Tomsolomon on 2008-05-05
And now the audio has changed back to working on the headphones and not on the speakers.... Go figure...:confused:

---

### Post by Tomsolomon on 2008-05-06
This fix works for my Laptop also L30-134 PSL-33e.

[http://ubuntuforums.org/showthread.php?t=473425&highlight=l30-134](http://ubuntuforums.org/showthread.php?t=473425&highlight=l30-134)

My advice is if you have a Toshiba Satellite audio problem look here first.

No speaker audio, no headphone audio
or a combination of the two.
And if your wondering about the way I've set out this post/? it's to make it easier for people to find if they are using the search tool.
I had terrible problems trying to find a solution to this problem, if only people would write the exact problem in the post somewhere.

---


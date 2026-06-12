---
title: "800*600, wont detect monitor, not in manual list, ENVY set screen black"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Rorke on 2008-06-23
Setup - 19in flat screen, 8.04 fresh install (now dual boot).
After getting some updates, I accidently screwed the graphics - which now won't go beyond 800*600. I was running as 1200 (?) or so.

I'm not running NVIDIA driver, but when I enable it, after rebooting I get a high res login screen then no signal. I have to power down and boot into the repair kernel and repair the Xserver. When it comes back it is in 800*600 again.

I don't need good graphics such as accelerated 3D, just a better screen res.

I've searched through posts for ideas, but I think I've just done something so trivial and basic that no one else ever reports it as a problem. Other 800*600 bugs seem quite involved and specific. This was all working until I messed around with the synaptic manager to ger proposed updates and installed a i386 kernel instead of a generic one. Not sure if that was what did it, or if trying to fix something else screwed it up worse.

My screen is installed as plug n play, and when I try to set it manually, the manufacturer is not listed.

I've tried setting different screen res sizes, but they all end up either blanc or crossed grey lines - even 800*600 when I set it manually.

My monitor is I-Inc, AG191D and I have Nvidia graphics card.

---

### Post by phidia on 2008-06-23
What specific nvidia card (model#) do you have, and since envy is in your subject line when did you install that? (before or after this problem appeared?)

If you had it working with higher rez then you are able to get now the first thing to do IMO is check your /etc/X11 directory for xorg.conf.bak files if you have a previous xorg.conf file you might be able to use that and get back to where you were.

> sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf 

If you have no back up (bak) files then you can try playing with > sudo dpkg-reconfigure xserver-xorg sometimes it takes several tries running that but that program will allow you to select all your video parameters. Have your card and monitor specs available.

---

### Post by Rorke on 2008-06-23
This is going to sound really thick, but where would I get my card and monitor specs from?

---

### Post by Rorke on 2008-06-23
> sudo dpkg-reconfigure xserver-xorg 
This doesn't seem to let me configure graphics, The first questions is about a framebuffer, then all the rest are about the keyboard. any ideas? I presume I need to enable the driver first or something, but in the hardware drivers section, I show 'No Proprietary drivers' and nothing to click on either.

---

### Post by phidia on 2008-06-23
To find your card type lspci -v in a terminal window.
The dpkg-reconfigure command I posted before does set up your video.
You need to go all the way through the program. I don't know whether the computer
you're asking about is a laptop or desktop but you should be able to google the model/manufacturer to get the specs.

---

### Post by Rorke on 2008-06-24
I am trying to configure 2 machnies.
One is called simon, the other is jackie.
On simon, lspci gives a lot of 'unknown device' and access denied. It is listed as follows:
lspci -v
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at ff00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c80 [size=64]
	Capabilities: <access denied>
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at eff00000 (32-bit, non-prefetchable) [size=512K]

00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: 66MHz, fast devsel

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at effff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1) (prog-if 20 [EHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at efffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f05b:0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: efb00000-efbfffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ea000000-edffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: efa00000-efafffff
	Prefetchable memory behind bridge: 00000000ef900000-00000000ef9fffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efe00000-efefffff
	Prefetchable memory behind bridge: 00000000efd00000-00000000efdfffff
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Foxconn International, Inc. Unknown device 0d1f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f700 [size=16]
	Memory at efff8000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: Foxconn International, Inc. Unknown device ff1f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	I/O ports at ce00 [size=256]
	Memory at efcff000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at efb00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ea000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bf00 [size=128]
	[virtual] Expansion ROM at ed000000 [disabled] [size=128K]
	Capabilities: <access denied>

---

### Post by Rorke on 2008-06-24
The dpkg command only has one question that isn't related to keyboard setup, and that is: Do I want to use the kernel frame buffer? Whether I answer yes or no, I still don't get any option to set any graphics. I suspect that something so obvious is missing that it is just not working properly.

---

### Post by phidia on 2008-06-25
> **Rorke said:**
> The dpkg command only has one question that isn't related to keyboard setup, and that is: Do I want to use the kernel frame buffer? Whether I answer yes or no, I still don't get any option to set any graphics. I suspect that something so obvious is missing that it is just not working properly.

This command > sudo dpkg-reconfigure xserver-xorg  should allow you to select a video card driver, adjust monitor settings and save the new settings to your xorg.conf 
Are you going all the way to the end of the program? Are you using that command with other parameters? (like phigh) Don't do that.

Going back to a fresh sheet of paper on this-did you check the iso you downloaded with md5sum?

BTW this > 02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA controller]) is your video card and it should be supported in ubuntu. 

Please take a look at the thread [here]("http://ubuntuforums.org/showthread.php?t=818064&highlight=geforce+8500+gt") and see if that relates to you. I think you should be able to get your video working correctly from that. 
Hardy seems to have caused some problems with recent updates.

---

### Post by avtolle on 2008-06-25
Try from the console```
gksudo displayconfig-gtk
```to get your screen identified and hopefully set your resolutions. The graphics tab will allow you to see if the correct graphics card is identified, and the ability in some cases to select the correct one.

---

### Post by Rorke on 2008-06-25
OK, thanks for the help - in the end I re-installed Ubuntu again in a new partition and took all the preferences over. It got all its own updates and now works fine! I guess it was a case of fiddling around with it and not knowing what I was doing.

Next project is to get Trigger going! (Seems to crash the whole system regularly)

---


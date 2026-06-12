---
title: "SiS card video interference"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by errummm on 2008-10-29
Hi. I have been using ubuntu for a while now (18 months), and have managed to head-butt my way through a few basic issues by following existing guides, but am now up against one which stumps me, in part because I don't even know how to describe it in a way a search engine would understand.

Yesterday I upgraded to 8.10 and since the upgrade, the display on my screen has contained a blue interference around certain shades of colour. In order to understand the problem, I set up my desktop background as a gradient from black to white and the interference appears in bands from the blacks to the midtones. The interference itself is semi-solid (slight flickering, but mostly stable) blue bands of varying thickness.

I'm really not sure where to even begin in my search for answers. I have an Acer Aspire 5004WLMi.

"lspci | grep VGA" gives me:
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

The same issue occurs whether I am logged in under gnome or kde. (I can't see any signs of it being an issue on the ubuntu splash screen, but there's a pretty limited colour range there to choose from)

I'm not sure what other information I should provide because I'm not sure what is the likely culprit.

Any help would be much appreciated.

---

### Post by errummm on 2008-10-29
Also, I just loaded an openSUSE 10.4 Live CD to test if it was a hardware problem, and it worked fine in there.

---

### Post by errummm on 2008-10-30
Please consider this an obligatory bump. Would this thread have a better home elsewhere?

---

### Post by Cristina Precioso on 2008-10-31
I have the _exact_ same problem.

My info: 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
	Subsystem: Elitegroup Computer Systems Device 0f52
	Flags: 66MHz, medium devsel, IRQ 11
	BIST result: 00
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at dfee0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at cc00 [size=128]
	Capabilities: <access denied>
	Kernel modules: sisfb


Take a look: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/6365](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/6365)

---

### Post by inferno1005 on 2008-10-31
I had the exact same issue as the rest of you, on a laptop with an SiS video card. The fix in the forum below solved my problem.

[http://ubuntuforums.org/showthread.php?p=6068699](http://ubuntuforums.org/showthread.php?p=6068699)

---

### Post by Cristina Precioso on 2008-11-01
Thank you so much.

I'm kinda new to this thing so I really don't know what that means.

[I]
Try
Code:

sudo modprobe sisfb

in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.

If that worked, then you can add sisfb to /etc/modules so that it will be loaded at startup.[/I]

Can you help me with a step by step, maybe? I'm pretty close to start crying here, haha.

---

### Post by Cristina Precioso on 2008-11-01
Thank you so much.

I'm kinda new to this thing so I really don't know what that means.

[I]
Try
Code:

sudo modprobe sisfb

in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.

If that worked, then you can add sisfb to /etc/modules so that it will be loaded at startup.[/I]

Can you help me with a step by step, maybe? I'm pretty close to start crying here, haha.

---

### Post by lH)4~mK0e on 2008-11-01
To get to a virtual terminal you would press and hold the Ctrl and Alt keys and press any of the F keys 1-6 (F1 F2 etc) doesn't really matter which one.  The normal screen is reserved at F7, so when you complete this step, they are telling you to do Ctrl and Alt and F7, then Ctrl and Alt and Backspace.  This makes the Xserver restart using the new module.

---

### Post by cool_penguin on 2008-11-08
Worked great for me on my Acer Travelmate 2310 notebook which comes with a crappy SiS integrated graphics card.

Now even the text that appears at shutdown seems to be high in resolution and sharp and the system now shuts down a lot faster.

sudo modprobe sisfb works great.

I also added it to /etc/modules and I no longer get a blank GMD login screen.

UBUNTU is great.

Cheers,
Harry

---


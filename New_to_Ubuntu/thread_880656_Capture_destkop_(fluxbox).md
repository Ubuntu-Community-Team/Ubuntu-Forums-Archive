---
title: "Capture destkop (fluxbox)"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-08-05
I need to do a video capture of my desktop, but for some reason non of the programs I tried will work when I'm using fluxbox.

When this machine was still using gnome, it worked fine.

Some of the error's I get.

recordmydesktop:

rw@legend:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be Fluxbox

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7acb767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7acb8b1]
#2 /usr/lib/libX11.so.6 [0xb7f24421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7f0c734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dea4fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ba3e5e]

I tried the following programs and nothing works:

xvidcap, recordmydesktop, istanbul.

I don't know if you need more info on the hardware, but here it is:

lrw@legend:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200
]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)

---

### Post by billgoldberg on 2008-08-05
Tried it with gtk-recordMyDestkop. It didn't work (no shocker there).

It never went above 0% after I stopped the recording.

---

### Post by AdamWood on 2008-08-05
Have you recently upgraded to Ubuntu 8.04?

I haven't been able to make a standard install of Ubuntu record on any desktop. There is some broken code in a library called libxcb.

It would be great to hear if you've managed to get it working under Gnome on a vanilla 8.04 though.

---

### Post by ByteJuggler on 2008-08-05
Do they (all the recording programs you tried) all generate the same/similar error?  The error suggests a problem in the software somewhere, we need to try and figure out whether this is a new bug introduced somewhere, or whether it is as a side effect of you not running a fully gnome system.  Not knowing any more I'd lean towards it being a bug rather than the lack-of-gnome's fault, but that's just a hunch which might be wrong.

---

### Post by AdamWood on 2008-08-05
It's an Xorg bug, there's already a fix for it but it hasn't been released as an update yet. I guess there's a chance it'll be in Intrepid Ibex.

Patching your system so that it works isn't an easy option.

---

### Post by billgoldberg on 2008-08-05
> **AdamWood said:**
> It's an Xorg bug, there's already a fix for it but it hasn't been released as an update yet. I guess there's a chance it'll be in Intrepid Ibex.

Patching your system so that it works isn't an easy option.

Are there patches available?

If you could provide a link, it would be great.

--

To answer a few questions:

yes all programs gave similar errors.

It did work on the same machine in a gnome a month ago, which is the last time I used gnome on this machine.

I've been using Ubuntu 8.04 on this machine since the day it came out, with all updates installed.

---

### Post by AdamWood on 2008-08-05
To be honest I wouldn't want to give directions to anyone that could seriously screw up their computer. This is an "Absolute Beginners" forum after all. ;) I don't run a normal Ubuntu installation so the patches I used wouldn't be applicable anyway.

If your intent on doing it you can find everything through Google by searching for XCB locking assertion bugs.

If you have to capture a fluxbox desktop I'd suggest you downgrade to 7.10 or 7.04 though for ease. I can't remember which worked best for screen captures off the top of my head.

---

### Post by billgoldberg on 2008-08-05
> **AdamWood said:**
> To be honest I wouldn't want to give directions to anyone that could seriously screw up their computer. This is an "Absolute Beginners" forum after all. ;) I don't run a normal Ubuntu installation so the patches I used wouldn't be applicable anyway.

If your intent on doing it you can find everything through Google by searching for XCB locking assertion bugs.

If you have to capture a fluxbox desktop I'd suggest you downgrade to 7.10 or 7.04 though for ease. I can't remember which worked best for screen captures off the top of my head.

Thanks for pointing me in the right directin with XCB.

I have a few computers in my house, and the one fluxbox is running on is the one I toy around with. So me trashing that computer isn't a big deal. 

I probably should have posted this in "general help" but I found the absolute beginners forum to be more useful because more people are active here.

---


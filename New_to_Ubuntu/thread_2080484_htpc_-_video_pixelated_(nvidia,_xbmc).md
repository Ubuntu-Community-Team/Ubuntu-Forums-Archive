---
title: "htpc - video pixelated (nvidia, xbmc)"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by vict00r on 2012-11-04
Hi.

I have just built a htpc based on a motherboard with builtin nVidia Geforce 6050(?) gpu and EVGA Geforce 210 pcie graphics card and I'm not satisfied with the video quality. I'm using the pcie-card.

This is what I have done so far:

-Fresh install of Ubuntu 12.04 Server (minimal)
-Installed nvidia driver version 304.60 from ppa.
-Disabled Extensions in /etc/X11/xorg.conf
-Tested video playback with mplayer2, reports using vdpau(!) (also "daily build"-ppa)

I'm not using any window manager, but start xbmc with the following command:
xinit xbmc-standalone

Playback of video is "pixelated", this is not tearing effect, but the whole display is affected. The effect can easily be seen when watching horizontal scrolling text as often seen on "BBC World". Playing back my video test file with the tv's builtin media player is perfect, but nothing I have tried on the htpc solves the problem.

Also the htpc boots to a black screen, pressing Ctrl-Alt-F* brings up the tty.

lspci | grep -iA2 vga:
```
03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
03:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```


How can I solve this problem?

---

### Post by vict00r on 2012-11-06
Solved:

Deinterlacing was off.

Set deinterlacing to auto: When playing live tv, click the screen, then click the small film reel icon in the lower right to get the video settings, then set deinterlacing to auto. Scroll down and select set as default.

---


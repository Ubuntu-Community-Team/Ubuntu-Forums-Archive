---
title: "GTX460 and ubuntu 10.04 hdmi no sound"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by fabrex on 2011-10-21
Hi. I have upgraded my graphic card from a gtx275 (with spdif cable for sound) to a gtx460 (both zotac). Sound through hdmi enction with my tv does not seem to work anymore. I've tryed installing an upgraded version of alsamixer, as described in one of te threads here in ubuntu forums, but it didn't work. When I type lcpci -v, the following section seems to be related to my nvidia card sound:

01:00.1 Audio device: nVidia Corporation Device 0beb (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 2166
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fbffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

But alsamixer simply does not list my gtx460 as a sound device, nor can I get the sound to work in any other way.
Any suggestions?
Thank you

---

### Post by tbrminsanity on 2011-12-24
Good day,

I was having a similar issue with my Ubuntu 11.10 install.  I also noticed that video was sped up sites like YouTube.  When I checked out my proprietary drivers, the main graphics driver was disabled.  I enabled the driver, and reset my machine.  Sound returned and video is being played at a normal speed.  Hope this sets you on the right track.

TBRMInsanity

---


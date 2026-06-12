---
title: "NO SOUND with Intel NUC Core i3 DC3217IYR Mythbuntu 12.04.3"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by anoldguy on 2013-10-21
Well, sort of [Solved].  I found a configuration that works: 

Mythbuntu 12.04.3 32 BIT 

HDMI plugged into the HDMI socket FURTHEST away from the LAN socket.  When plugged into the HDMI socket closest to the LAN socket, no audio.

Sound when using my new LG big screen TV.  It still has no sound on my older Olevia big screen TV.

----------------------------------

Initially with Mythbuntu 12.04.3 64 bit, tried again with Mythbuntu 12.04.3 32 bit.
MythTV recording plays fine except for no sound.  VLC plays an MP3, but no sound either.

The HDMI cable (purchased this year) works with my Apple TV, and BlueRay player.

Tried both HDMI ports on the Intel NUC.

Tried Settings, Additional Drivers; nothing found.

Tried downloadcenter * intel * com Nothing for DC3217IYR

In Terminal in  alsamixer, 
Card: HDA Intel PCH
Chip: Intel PantherPoint HDMI
Item: S/PDIF
  00           00
S/PDIF  S/PDIF 1

This Intel PC (NUC) does not have audio connections; it's through the HDMI.  Have I bought a PC that can't produce sound in Linux?

---


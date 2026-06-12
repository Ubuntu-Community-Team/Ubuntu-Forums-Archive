---
title: "Crap wav exports in Ardour"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by originalsynthesis on 2008-09-04
Hi there, just recently started using Ubuntu studio and have been enjoying it. This is my first install of a linux OS, so I'm pretty green to the whole scenario. Im fairly proficient with computers in general, though being spoon fed by windows all these years has whittled me down to a certain kind of helplessness now that im on linux. So, I hope you'll bear with.   
  My prob right now w/ Ardour is that when i export projects to .wav, in any bitrate/sample rate, it will come out clipped and glitchy. A sub-issue that slowed me down at first, was getting files with length, yet no sound whatsoever. I fixed that by specifying in the export menu all the tracks i want. I dont see why it didn't just export through the master outs. everything in jack was connected AFAICT
  As for the main issue, iv tried running on rt and generic kernels with no result. I changed my memlock to 65%, then to 50%, which helped oh so slightly. I played with 16,24, and 32 bits, and all the sampling rates (using dithering when doing so). Though i haven't tried files other than WAVs.
 Here's my humble little laptop machine:
Toshiba Satellite p25 s509
2.8 ghz p4
*512m RAM
*realtek ALC202 sound
*80 gig hard drive( though the linux partition is nearly full)

the last three items are what im thinking the problem is coming from, though the memory and sound card are the main issues i see.  although, maybe increasing my partition size would help, dunno. What do y'all think?

---


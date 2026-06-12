---
title: "Heaphone Jack broke off - need to bypass Heaphone Jack sensor"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by infosociety on 2012-10-25
Hello Everyone,

Regretfully, my son broke his headphone jack inside my computer.  I was able to by pass easily on the windows side, however having a bit of a harder time on the Ubuntu 12.04 side.  Here's my information
 
[http://www.alsa-project.org/db/?f=ffb39be9a59e5a79f3cc4f5e39ecdff3644f6e01](http://www.alsa-project.org/db/?f=ffb39be9a59e5a79f3cc4f5e39ecdff3644f6e01)

when lspci - 01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]

cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbcf8000 irq 43
 1 [CinemaTM       ]: USB-Audio - Microsoft® LifeCam Cinema(TM)
                      Microsoft Microsoft® LifeCam Cinema(TM) at usb-0000:00:1d.0-1.4, high speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdbc000 irq 44


If anyone could lead me to a guide (I've read quite a bit of threads, but I'm having a hard time figuring it out as I'm a complete NOOB.
or a quick walk through that would be great as I would love to learn more about the way it works..

Hopefully this helps, as I am loving Linux, but would also love to hear music while I work and figure Linux ubunt12.04

---


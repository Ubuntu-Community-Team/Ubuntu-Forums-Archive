---
title: "Speakers and Headphones play at the same time"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by nikolesturm on 2012-09-21
Bought my Toshiba satellite E305, model # PSE30U-00D001-windows 7 Blu ray player etc latpop last week. Decided to install Ubuntu as a dual boot on the hard drive. 
Whenever I'm using the ubuntu side, and  I plug in my headphones, my speakers continue to play.  (this doesn't happen on the windows side, the headphones plugged in auto mute the speakers)
I've installed Gnome alsa mixer, and the mixer doesn't give me a headphone option.  Just master, pcm, mic 1, and mic 2; At the bottom it shows IEC958 as a checkbox.

This is the version I'm running
~~~~~~~~~
Linux ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
~~~~~~~~
 lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fcb3
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at c2700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
~~~~~~~~~

when I'm on the windows side I check out drivers that say "Audio" 
I get:

Conexant SmartAudio HDdriver provider: conexant
driver date: 12/6/2010
 driver version: 8.46.0.0
digital signer: microsoft windows hardware compatibility publisher




or


 Intel(R) Corporation display audio 
driver date: 10/15/2010
 version: 6.14.0.3074


or


high definition audio controller
provider: microsoft
date: 11/19/2010
version: 6.1.7601.17514

~~~~~~~

I've checked out other threads with similar issues, but since I'm new at this linux business, they implied a lot of "already should know codes" or the issues still weren't solved.

Any help would be greatly appreciated!! Aside from this issue, I'm loving Ubuntu and would like to make it my full time os.

---


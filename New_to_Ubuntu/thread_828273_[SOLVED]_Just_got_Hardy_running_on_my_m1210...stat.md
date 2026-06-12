---
title: "[SOLVED] Just got Hardy running on my m1210...static in left headphone?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by gohanssjn on 2008-06-13
For some reason, with my headphones, i get static in the left ear wehn using any audio driver in Ubuntu.

The laptop is a Dell m1210, and everything else seems to work.  is this a known thing...or could my hardware be going?

---

### Post by gohanssjn on 2008-06-13
Interesting, maybe it is Ubuntu, my left speaker sounds the same...

---

### Post by gohanssjn on 2008-06-13
Hmmm, uninstalled all GStreamer plugins and it is gone, even in the ALSA test tone.

So...which ones should I install to get media playback then?  Mainly DVD's, mp3's, and m4a's?

Any help is greatly appreciated!

EDIT:  Huh, well it all still plays...are the gstreamer's superfluous in Hardy?

---

### Post by SJrX on 2011-10-30
So I solved this problem years ago, and then I reinstalled and forgot. Today I solved it again. This thread comes up often when I search so I'll put your solution here.

The Chip on the M1210 is:  SigmaTel STAC9221 A1.
It comes up on lspci as: Intel Corporation N10/ICH 7 Family High Definition Audio Controller

The solution is to run alsamixer (or whatever you are using), and mute the S/PDIF channels. (You actually have to mute them).  Specifically my system running Natty Narwhal has an S/PDIF and S/PDIF Default showing up under AlsaMixer v1.0.24.2. By default they should up as 00  00 with no bar. If you mute the S/PDIF channel it's fine.

---


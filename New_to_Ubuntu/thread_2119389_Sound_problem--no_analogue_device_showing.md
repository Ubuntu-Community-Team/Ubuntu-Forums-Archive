---
title: "Sound problem--no analogue device showing"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by pjyonweb on 2013-02-23
I recently installed Ubuntu 12.04 for the first time on Dell E1405 laptop.  I played a song on Rhythmbox thru the laptop speakers just fine.  Later I went into Sound Settings and clicked on the only device showing under "Play sound through"--that device was Digital Output (S/PDIF) Built in audio.  When I tried to play a song, there was no sound through laptop speakers.  There appears to be no way to return to the previous device or unselect the Digital Output.  

I ran aplay -l and received this:
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So the single card (motherboard sound) has device 0 as Analog and device 1 as Digital.  But I cannot get device 0 to show as available in the "Play sound through" list.

I also tried reinstalling alsa, but there has been no change.  
Thank you.

---


---
title: "[SOLVED] Volume control with USB Headset &amp;amp; Intrepid"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-10
I downloaded Intrepid this morning & I have no control of the volume on the USB headset. The unit is a 'Gigaware' Headset with mic. It has it's own volume control in addition to the system volume control... Neither work. I have sound, it's just too loud. Is there a soft control I need to toggle ?

---

### Post by Bölvaður on 2008-11-10
Double click the volume control, type "gnome-volume-control" into the terminal or into the box from Alt+F2

ok with volume control open you go into File &#8594; Change Device and look for USB Audio (Alsa Mixer)
There could be more than one speaker control depending on your device.. I have "speaker" and "speaker 1"

When I have "Speaker 1" set few pixels from minimum volume, the volume is perfect.

---

### Post by JKBurton on 2008-11-10
I dealt with this one last weekend. I learned there's a bug in Gnome's volume control where it doesn't see (some?) USB sound devices. 

The fix is: "sudo apt-get gnome-alsamixer". It'll show up in Applications/Sound & Audio. Just use that mixer instead of the built-in ones and it works fine...at least for me.

My volume is fine now, but the volume +/- buttons on my keyboard and on the headset are incorrect. They do control volume, but the wrong ones :)  I haven't looked at that one yet to see if I can fix it. Maybe next weekend.

Best of luck,
Keith

---

### Post by CoCoKnots on 2008-11-10
That's Great... Thanks for the guidance. This just gets better all the time.

---


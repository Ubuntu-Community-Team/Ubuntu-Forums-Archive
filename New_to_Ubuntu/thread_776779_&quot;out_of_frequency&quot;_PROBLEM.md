---
title: "&quot;out of frequency&quot; PROBLEM"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Shnooky on 2008-04-30
K...My monitor was just working no more that 1 hour ago and now it is just giving me the "Out Of Frequency" box thats floats around your screen in purgatory.  Ive tried recovery mode and hitting auto/select button on the Envison flat screen monitor.

When i boot up the computer it is fine but right after ubuntu loads and is just about to go to the log in screen the "box-o-death" appears...

idk what to do

all help is appreciated, thx

-shnooky

---

### Post by hardyn on 2008-04-30
I cant tell you exactly what do to, as i am not infront of my machine; but i can tell you where to look.

you monitor is working... but something has altered the vertical refresh of your video output... did you change video modes?  If we assume that your monitor has a maximum scan frequency of 70hz, for whatever reason your video card is ouputting at >70hz; and the monitor is rejecting the input as protection against damage.

boot into recovery mode, or whatever they call it, and you will have to edit the xorg.conf file, or perhaps another menthod (i am not running hardy and am not familliar with bullet-proof X) to force your scan rate down.

the other option is to perform the dkpg-reconfigure (search for it, i am not familliar with the exact syntax) to reset the display mode of the X server.

that should take care of it.

good luck.

---

### Post by Shnooky on 2008-04-30
also i tried to boot from the disk and do it in safe graphics mode but it stops after the 5 checks where it says ok on the far right

---

### Post by Shnooky on 2008-04-30
idk if ur looking at this hardyn but i repaired the X server and it worked so thx

---


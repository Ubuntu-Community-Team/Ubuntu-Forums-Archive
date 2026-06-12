---
title: "Synaptics Dual Mode"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mecanologo on 2008-04-26
Hello!!
I've just set up Ubuntu on my new laptop, and it rocks. One thing I dunno about it is how to enable Synaptics Dualmode touchpad.
The other, is that my volume is quite low, even when I set it to its highest point. I've got a laptop with a 5.1 Dolby integrated (Harman/Kardon)
Thanks

---

### Post by dokdoom on 2008-04-26
Not sure about the touchpad, I would just google that. For your volume, run

alsamixer

and use your arrows to move around and turn the "switches" up. The two you are probably going to look for are the 'Master' and 'PCM' "switch". To turn on the switches just hit the spacebar if for some reason there is one you need turned off. Hit ESC to exit alsamixer. Hopefully that fixes your audio problem, always does for me.

---

### Post by dearingj on 2008-04-26
Regarding your volume:

Right-click on the volume control icon (upper right corner of the screen by default) and choose "Open volume control". A window should pop up with several volume sliders, try adjusting some of them. I find that "Master", "PCM", and "PCM Front" all affect sound volume on my computer.

---

### Post by mecanologo on 2008-04-27
Thanks!
Excellent!

---

### Post by mecanologo on 2008-04-27
and do you think sometihg can be done about the dual mode.

---

### Post by dearingj on 2008-04-27
I don't know.. Have you tried installing gsynaptics?

---

### Post by mecanologo on 2008-04-27
GSynaptics couldn't initialize
You have to set "SHMConfig" 'true' in xorg.conf....
buttt.... I don't have that in my Xorg.conf
Thanks

---

### Post by dearingj on 2008-04-28
I got GSynaptics working on my laptop. Here's the relevant section of my xorg.conf (I use a Synaptics touchpad too):
```

Section "InputDevice"
   Identifier   "Synaptics Touchpad"
   Driver       "synaptics"
   Option       "SendCoreEvents"      "true"
   Option       "Device"              "/dev/psaux"
   Option       "Protocol"            "auto-dev"
   Option       "HorizEdgeScroll"     "0"
   Option       "SHMConfig"           "true"
EndSection
```
I added the SHMconfig line manually, the rest were already there.

---

### Post by mecanologo on 2008-04-28
how can I edit it?
I can't save it.!
Thanks!

---

### Post by ner0tic on 2008-04-28
> **mecanologo said:**
> how can I edit it?
I can't save it.!
Thanks!
> 
sudo gedit /etc/X11/xorg.conf

you need root access to save it.

---

### Post by dearingj on 2008-04-28
Open a terminal and type 
```
sudo gedit /etc/X11/xorg.conf
```

eidt: I see ner0tic beat me to the punch :)

---

### Post by mecanologo on 2008-04-28
sudo: unable to resolve host jose-laptop

---


---
title: "I am without sound"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by angel2121 on 2008-08-26
I also have no Idea where to begin to look to troubleshoot because apparently there aren't driver's needed for the hardware in my toshiba a65 s-126, like there are in windows? and I've been using linux for like 3days can anyone point me in the right direction?

---

### Post by tuxxy on 2008-08-26
Try editing the settings at **system > prefs > sound** eg ALSA for output

---

### Post by nicedude on 2008-08-26
try running the following in a terminal window and make sure that sound is turned up here.

sudo alsamixer

If you dont know how to open a terminal then Applications -> Accessories -> Terminal will do it, then paste the above and hit enter. If once there the bars are not turned up then turn them up and you may have sound all of a sudden :-)

Don't know why but on 1 of my Ubuntu systems mutes itself in this way every once in a while ( almost like it wants me to remember that command :-) ) 

Hope this helps fix it

---

### Post by angel2121 on 2008-08-30
awesome thank you guys ! works great !

---


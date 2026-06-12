---
title: "need sound help. soundcard: Intel ALC861. Zepto Computer."
date: 2008-10-06
forum: New to Ubuntu
---

### Post by mag_luca on 2008-10-06
Ive been fooling around with my sound in Ubuntu.
I can get sounds from my computer, but the sound adjustments are not working. 

From the terminal i can detect a Intel ALC861 soundcard on a Zepto Computer.

Im pretty new to linux, and been trying some different changes - but i cant make it work.

Someone out there got any suggestions?

PEACE.

---

### Post by markbuntu on 2008-10-06
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can also look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Start in Post #2 here:

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)


These links are from my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by orawax on 2008-11-07
I managed to solve my microphone trouble with Realtek ALC861 in Fujitsu Siemens Amilo. Upgrading Ubuntu (or ALSA only?) and editing /etc/modprobe.d/alsa-base seems to give a host of new switches and controls...

See [http://ubuntuforums.org/showthread.php?t=943791](http://ubuntuforums.org/showthread.php?t=943791)

---


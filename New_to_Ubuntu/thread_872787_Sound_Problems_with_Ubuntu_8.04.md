---
title: "Sound Problems with Ubuntu 8.04"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by fenT1 on 2008-07-28
Hello,

I recently installed Ubuntu 8.04 on a Dell precision 650, everything works fine except the sound. I tried many commands and many forums but no results. Audigy2 available 

05:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
Subsystem: Creative Labs Unknown device 1003
Flags: bus master, medium devsel, latency 64, IRQ 23
I/O ports at ccc0 [size=64]
Capabilities: <access denied [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by argail1980 on 2008-07-28
you have to make some minor changes in the file /etc/modprobe.d/alsa-base.

Best search this forum for threads containing this file name and something like 'snd_hda_intel', it is full of people with the same problem

---

### Post by dew5 on 2008-07-28
Try going to System>Preferences>Sound

you sound card should bethe one selected.

also try altering the 

/etc/modprobe.d/alsa-base

file.

dew

---

### Post by dew5 on 2008-07-28
Also try this

speaker-test -Dplug:surround51 -c6 -l1 -twav


it test you speakers

dew

---

### Post by dew5 on 2008-07-28
and this one

speaker-test -Dplug:surround51 -c6 -l1

dew

---

### Post by AFarris01 on 2008-07-28
theres a pretty good comprehensive sound troubleshooting guide that will probably help you out... my direct link is currently broken, however heres a link to the forum post that has, basically all the same info:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+troubleshooting+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+troubleshooting+guide)

I will say though, before you read this through, check and see if the sound works when you boot up with a liveCD.  if it doesn't, then theres a good chance your sound card isn't currently supported (i had this problem with my laptop)

hope this helps!

Andrew

---

### Post by fenT1 on 2008-07-28
Thanks for your help guys but i had already tried these methods with no success, it seems as mentioned by dew that my sound card is not supported. Again i would like to thank you for your time.

---


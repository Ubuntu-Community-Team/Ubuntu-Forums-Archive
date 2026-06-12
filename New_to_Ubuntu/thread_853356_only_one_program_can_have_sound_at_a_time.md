---
title: "only one program can have sound at a time"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Kedster on 2008-07-08
if i am listining to music with rythmbox and i want to listen to a video on youtube i have to compleatly close rythmbox and firefox then start firefox and go watch the movie. this is just and example its the same with all programs im using hardy haron

---

### Post by kansasnoob on 2008-07-08
From 8.04 Release Notes:

> Some users report problems with video playback in the GNOME movie player, and audio playback in other applications, due to an error when connecting to the PulseAudio sound server. Investigation of this possibly hardware-specific issue is ongoing. A workaround is to enter the System -> Preferences -> Sound dialog and change the Music and Movies sound playback option from 'Autodetect' to 'ALSA'. 

I'm not sure that will help but it's worth a try.

---

### Post by Kedster on 2008-07-08
thank you very much that worked very well lol now ubuntu is almost perfect

---

### Post by sam198923 on 2009-02-14
Worked, Thanks a lot. Last thing i needed to do was to set the Default Mixer Tracks to the HDA (alsa mixer). But other then that my sound is finally working great, except for it still playing through my speakers while my headphones are plugged in. Im one step closer thanks to you.

---


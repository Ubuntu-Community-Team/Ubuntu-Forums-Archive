---
title: "Audacity won't record on my Hardy H. Desktop"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by peaceforall on 2008-10-09
Please help?

---

### Post by tjwoosta on 2008-10-09
in audacity go to edit-preferences  then change the recording device

---

### Post by peaceforall on 2008-10-09
Here are my options for recording: alsa default, alsa spdif, alsa:hda ati sb: alc833 analog (hw:0,2), alsa:hda ati sb: alc833 analog (hw:0,1), alsa:hda ati sb: alc833 analog (hw:0,0), oss: /dev/dsp

Which one should I choose?

May playback options are: alc833 analog (hw:0,1), alsa:iec958, alsa: spdf

Which playback should I choose?

---

### Post by kubug on 2008-10-11
Hi there,

I struggled with that just now as well. The way I got it to work actually was with the "Volume Control" applet. 
Click on Preferences, and then check on all the controls (I know, very precise, eh?). 
Then click on the recording tab, and bring all the bars up that are visible. Play with that until you can see things appear in your recordings in audacity.

Oh, and leave audacity on the OSS. It seems to work best with that, since it's programmed for that.

This is what I did to make it work. Hopefully it will work for you too. Cheers.

---


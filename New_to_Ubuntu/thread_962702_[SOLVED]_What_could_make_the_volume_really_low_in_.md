---
title: "[SOLVED] What could make the volume really low in Ubuntu?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by psam3 on 2008-10-29
I checked the master volume and the volume on the music player but I still can't get the volume high enough to really hear anything. Is their anything that could cause this?

---

### Post by chazn85 on 2008-10-29
what do you see if you go to system>prefs>sounds are you using alsa for the sound?

---

### Post by SuperSonic4 on 2008-10-29
Have you tried another file?

Also have you tried another source of sound such as flash

Lastly what is the audio output (ie speakers, headphones)

---

### Post by psam3 on 2008-10-29
It says autodetect on all of them. I'm using speakers hooked to a receiver which gets the audio from the computer.

---

### Post by chazn85 on 2008-10-29
ive had similar things at various times.  try changing them all to alsa first of all and see if that makes a difference.  then you can always change the volume using alsamixer via the command line

---

### Post by sayems on 2008-10-29
Double-click on "Volume Control" and check your setting, sometime speakers and headphone volume is too low. just to make sure their up

---

### Post by ajgreeny on 2008-10-29
In addition to what sayems said, check that the PCM level is not too low.  I usually find that a setting of 80% or 90% is about right for that.  If I set it at 100% there is a bit of distortion on the speakers.

---

### Post by psam3 on 2008-10-29
Thanks Everyone

---


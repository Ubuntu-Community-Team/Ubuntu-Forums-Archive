---
title: "Sound Recorder won't turn off"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-05-12
When I record with gnome-sound-recorder 2.91.2, (known as Sound Recorder on my Lubuntu system menu), it won't turn off and I have to kill it.

I'm using mplayer in gnome-media (I had to install PulseAudio Volume Control and then select Sound Recorder)

My system is 
Ubuntu 11.10
uname -a
3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by Kevin McCready on 2012-05-12
I've ditched "Sound Recorder" and managed to record from the terminal with 

arecord  -f  cd -t wav t.wav

but the sound was too soft when I played back with

aplay t.wav

Does anyone know how to adjust the recording level of arecord?

---


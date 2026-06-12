---
title: "sound in skype"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Old-un on 2012-03-18
Have been trying to configure Skype so that i can make video calls. The webcam works great but i can't get the sound? The only option under sound devices is: PulseAudio server (local) which doesn't work? Could someone help me please. Thanks

---

### Post by Rodney9 on 2012-03-18
Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal

---


---
title: "Sound capture/recording stops on high system usage"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by filu on 2012-08-27
I'm running Ubuntu 12.04.1 and i'm an 'mid-advanced' user, so my terminology may not be correct here.

System records (captures?) sound from the external microphone normally (checked with arecord). However, when I start any 'heavier' app (like firefox) it stops recording (arecord hangs). This is especially annoying while skyping as I can't do anything during the talk and sometimes the capturing stops even without any action during skyping (suddenly the person stops hearing me).

In case if this happenes I close skype (otherwise it hangs upon the next step), type "sudo alsa force-reload" and the capturing (recording?) works again until the same thing happens.

The problem occured on my computer since the first ubuntu install: with 10.04, then after its reinstallation and again after the upgrade to 12.04.1 (no problems with win XP before).

---


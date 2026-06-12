---
title: "[SOLVED] Lost Sound in VLC"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by TSS on 2008-07-27
Hey all,

While VLC still is able to play videos, there is no sound.  Videos play fine via Firefox with sound.  I tried removing VLC and reinstalling it, but that did not fix the problem.  I'm pretty sure I was able to play movies with VLC just fine only a few days ago.  The only thing that I can this of is that I just recently installed restricted plugins for certain formats.  Any thoughts on how to go about troubleshooting this?

---

### Post by Vivaldi Gloria on 2008-07-27
> **TSS said:**
> Hey all,

While VLC still is able to play videos, there is no sound.  Videos play fine via Firefox with sound.  I tried removing VLC and reinstalling it, but that did not fix the problem.  I'm pretty sure I was able to play movies with VLC just fine only a few days ago.  The only thing that I can this of is that I just recently installed restricted plugins for certain formats.  Any thoughts on how to go about troubleshooting this?

Goto the settings of vlc, find sound output modules (alsa, oss, pulse etc.). Choose a different one, save settings, restart vlc. One of alsa or pulse should work. Try all anyway.

---

### Post by TSS on 2008-07-27
> **Vivaldi Gloria said:**
> Goto the settings of vlc, find sound output modules (alsa, oss, pulse etc.). Choose a different one, save settings, restart vlc. One of alsa or pulse should work. Try all anyway.

That did the job.  Thank you :-).

---

### Post by Vivaldi Gloria on 2008-07-27
> **TSS said:**
> That did the job.  Thank you :-).

You're welcome.

---


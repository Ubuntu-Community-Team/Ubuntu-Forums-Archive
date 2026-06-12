---
title: "Video playback errors"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by gokurab on 2008-06-10
OK, I just got this problem and I tried everything to fix it but nothing helps. Whenever I try to open an AVI file from my hard disk, it opens in totem and mplayer, but there's no streaming and there's no seeking. Also, there's the same problem with video playing sites like youtube and tudou. The exact problem is that I load a video in the player, something comes up but doesn't play. I tried Totem, mplayer, vlc and amarok; all except vlc have the same problem, vlc crashes. I tries removing and adding the plugins but that didn't help. Any suggestions for this.

---

### Post by Sinkingships7 on 2008-06-10
Run this command and see if it changes anything:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---


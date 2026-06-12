---
title: "Noobie can't get no sound =O"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Trotzkii on 2008-09-18
I've been running ubuntu on my laptop on and off for about 3 weeks now... it's a second OS I have on my computer (the first is XP).  So, I'm really new on the whole Linux OS scene.  Lately it's come to my attention that I simply cannot play audio files... no matter which audioplayer I use, it just seems to either cycle through my songs without actually playing them, or the program freezes... Btw, movies and internet videos/media seems to work fine... it just seems to be playing mp3 files that poses a problem right now... Any suggestions as to what I ought to do?  Many thanks =)

---

### Post by hellion0 on 2008-09-18
Try installing mpg123:

```
sudo aptitude install mpg123
```

and try playing a mp3 with it:

```
mpg123 /path/to/file.mp3
```

If it works, you need the proper codecs for your music player.

---

### Post by Perfect Storm on 2008-09-18
You might find this useful: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by markbuntu on 2008-09-18
If you need a total multimedia overhaul follow this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If you just want the plugins and w32codecs and libdvdcss2 to play restricted formats follow this guide:

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

These will get you everything you need to play just about any audio/video format.

---


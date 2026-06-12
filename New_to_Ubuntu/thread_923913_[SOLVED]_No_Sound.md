---
title: "[SOLVED] No Sound?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Gannon8 on 2008-09-18
I boot up my computer and there is no sound. None from youtube, which usually works, from any of my games, or my audio player. I have some ubuntu-studio packages installed by the way, I think they install a sound server?

---

### Post by tuxxy on 2008-09-18
Can you hear the test sound file play, in sound properties

Also you could open a terminal and try

```
aplay /usr/share/sounds/startup.wav
```

---

### Post by Gannon8 on 2008-09-18
No, no output. :(

---

### Post by Gannon8 on 2008-09-26
Bump

---

### Post by pyromanic123boom on 2008-09-26
Open up alsamixer

alsamixer

in terminal, and boost Master up to max. It may be one of those in alsamixer, so just play with it. It's probably just your master is low, and so nothing is playing.

---

### Post by markbuntu on 2008-09-26
Try my guide. Since you have Ubuntu Studio, you also have the jack audio connection kit which is sort of a sound server and can conflict with your other applications if not setup properly. There is a jack section near the bottom of my guide. You should read it and follow the links. It probably would not hurt to read all the sections that seem relevant to you.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Gannon8 on 2008-09-27
Yeah, after I installed ubuntu studio I had to change a setting to make it work. Anyway, I got it working. The Line volume was all the way down.
Thanks :)

---


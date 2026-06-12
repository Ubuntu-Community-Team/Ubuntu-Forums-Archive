---
title: "Can play internet flashplayer, and music, but not both"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Marfish on 2008-08-01
Hey, every time I boot up my computer I have to either choose whether I want to use youtube while I on, or playing my music. Once I choose either one, the other doesnt have any sound. If I play a movie on youtube, my music wont play, if I choose my music, the sound for the movie on youtube wont play. Is it something to do with my codecs? Does anyone know what I should do? Any help will be greatly appreciated.

---

### Post by Ryadt on 2008-08-01
Try ending pulse audio. ```
killall pulseaudio
```

---

### Post by Marfish on 2008-08-01
That did the trick, both are even working at the same time! Thanks very much!

---


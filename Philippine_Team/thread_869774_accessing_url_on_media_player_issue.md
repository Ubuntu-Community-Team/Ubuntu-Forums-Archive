---
title: "accessing url on media player issue"
date: 2008-07-25
forum: Philippine Team
---

### Post by killer_d76 on 2008-07-25
guys what do you think is the best media player in ubuntu 8.04 to play/access this url ```
rtsp://204.2.168.70/broadcast/dzbb.rm
``` i tried VLC, MPlayer and Rythmbox to launch it, but unfortunately they all sounded the same.. like radio being played inside a tunnel :lolflag:, but when i tried it on VLC on XP, it worked like a charm and without hick-up! :confused: even with youtube playing on the side!.. by the way that's a local radio station (DZBB) that i usually listen to rather than reading newspaper.. thanks

---

### Post by ache109 on 2008-07-25
> **killer_d76 said:**
> guys what do you think is the best media player in ubuntu 8.04 to play/access this url ```
rtsp://204.2.168.70/broadcast/dzbb.rm
``` i tried VLC, MPlayer and Rythmbox to launch it, but unfortunately they all sounded the same.. like radio being played inside a tunnel :lolflag:, but when i tried it on VLC on XP, it worked like a charm and without hick-up! :confused: even with youtube playing on the side!.. by the way that's a local radio station (DZBB) that i usually listen to rather than reading newspaper.. thanks

ano po yan radio station? try nyo rhythmbox....

---

### Post by king leoric on 2008-07-25
Have you tried built in totem???

---

### Post by loell on 2008-07-25
try to increase VLC's buffer in

**settings** --> **preference** --> **input/output codecs** --> **access modules** --> **file**

maybe try 500 or more? instead of the default 300.

---

### Post by killer_d76 on 2008-07-25
thanks guys.. i've tried rythmbox.. pero ganun din ang result, it sounded like a radio inside a tunnel, i haven't tried totem yet, i'll try testing your settings loell and let see if that should fix the problem.. i'll keep you posted guys, thanks ;)

---

### Post by killer_d76 on 2008-07-25
hhmmm.. VLC don't support the url that i want to use.. but the good thing is, when i tried using "gxine".. it works flawlessly! :popcorn: and the streaming audio sounds just right, no buffering even when i'm downloading videos from youtube! :KS:KS:KS

---

### Post by killer_d76 on 2008-07-31
okey.. i was still having issue with this streaming url ```
rtsp://204.2.168.70/broadcast/dzbb.rm
```

gxine did worked flawlessly before but after sometime of using it, i noticed some stopping and at some point it hanged!, i've tried all the media player available on synaptic but nothing worked better than VLC on windows :confused:, so what i did i downloaded the VLC installer for windows and install it on using wine app, and guess what?.. it's working! :lolflag:, i guess some things really work well on Windo$.

---

### Post by loell on 2008-07-31
weird case :D

---


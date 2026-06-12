---
title: "Visual effects and video playback pb."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by baldino on 2008-06-07
hi
i have ubuntu 8.04 hardy, a gefroce 7600gt with the drivers from envycg installed 
when i activate visual effects (even the lowest "normal" setting) it seriously affects video playback in VLC, mplayer and Movieplayer...
in fullscreen, i can see some horizontal "break lines" i'm not sure how to explaiin that correctly: it seems like 1/3 of the screen is refreshing faster (or slower) as the rest, and i see the picture "broken" when there is a fast motion...
and this completely disappears when disbaling all visual effects
i tried all possible video outputs: x11 gl xv but nothing does...

someone knows what i could do here ? ubuntu is not that good without some basic visual effects !

thx a lot

---

### Post by baldino on 2008-06-07
ok i found a solution all by myself !
check it here:
[http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)
[I]
If you're experiencing performance sluggishness, try starting compiz with the --loose-binding option. With loose binding, textures are enabled when created, and the nvidia driver seems a bit slow when binding textures, which is why this option yields a significant performance improvement.[/I]

that made the trick:popcorn:

---


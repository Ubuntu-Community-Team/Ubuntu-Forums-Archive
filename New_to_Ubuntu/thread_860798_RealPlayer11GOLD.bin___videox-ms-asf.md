---
title: "RealPlayer11GOLD.bin   video/x-ms-asf"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by mdocampo on 2008-07-15
I download Realplayer11GOLD.bin and after surfing the net I  was able to install it. it appear on the application menu under sound and video. It took a couple of days and I almost finish blind but I was so glad of being able to install something so weird like a bin file ....But happines doesn.t last and the player does not play at all video streaming or dvds. The play menu (Play Pause Stop Now Playing ...) appears always gray and the bottons appears also gray. When I try to open video streaming copying the URL in the open location menu I got
Component Missing The following components are required video/x-ms-asf. I heven,t been able to fix the problem downloading this component.:KS

---

### Post by tamoneya on 2008-07-15
The easiest way is to just install realplayer through the repositories,  In terminal just type:```
sudo apt-get update
sudo apt-get install realplayer
```

---

### Post by oldos2er on 2008-07-15
mdocampo, I believe you need to install the w32codecs (w64codec if you're running 64-bit).

---

### Post by jimmy the saint on 2008-07-16
realplayer isn't in the repositories

---

### Post by RomeReactor on 2008-07-16
Despite what the [official site]("http://www.real.com/linux") states, RealPlayer 11 [does not play WMV files]("https://helixcommunity.org/projects/player/forums/entry/3296"). It *can* play OGG, MP3, RM, and RAM.

---


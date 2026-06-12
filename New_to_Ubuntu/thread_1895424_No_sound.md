---
title: "No sound"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by kevbuntude on 2011-12-14
Hey.  I'm running Ubuntu 11.04 on my Macbook.  The internal speakers work, but when I plug in external or headphones there's no sound.  I'm pretty illiterate with ubuntu, so please, if someone could help me in simple terms that would be awesome.
Thanks.
Kevbuntude

---

### Post by kevbuntude on 2011-12-14
So I've been searching forums and I tried typing this in:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

and I got this link to my ALSA information:   [http://www.alsa-project.org/db/?f=3abe4afd79562087c39feb2f7314c8e2d0439e04](http://www.alsa-project.org/db/?f=3abe4afd79562087c39feb2f7314c8e2d0439e04)

Does this help?

---

### Post by kevbuntude on 2011-12-14
So I've been reading about this for hours, but the solution was just to download GNOME ALSA Mixer from the software centre and "uncheck" mute under "speaker".  Who'd-a-thunk?

---


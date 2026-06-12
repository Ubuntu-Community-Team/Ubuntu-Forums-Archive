---
title: "Boot Scripts"
date: 2008-07-01
forum: Programming Talk
---

### Post by moosehadley on 2008-07-01
Would anyone know how to create a boot script that would play an ogg file while the system boots? (much like Sabayon)

---

### Post by dtmilano on 2008-07-01
Add something like
>  mplayer -vo null /usr/share/gnome-games/sounds/bonus.ogg < /dev/null > /dev/null 2>&1

to an init script, for example /etc/rc.local.
Of course you need mplayer installed.

---


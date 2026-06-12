---
title: "I just want to watch TV"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by apienk01 on 2008-11-20
I am really frustrated. :mad:](*,) My analog/digital TV stick (Pinnacle Hybrid Pro clone) just won't show me analog TV. Digital TV works with mlayer, xine and me-tv (great app, recommended). The card is fully recognized by the system (Intrepid amd64). I can scan and tune analog channels from the command line using scantv, tvtime-scanner, and ivtv-tune, but when I try to watch them - nothing there. Mplayer just shows a green screen with a few flickering pixels, tvtime shows a black screen and is not responding, zapping just segfaults (it seems it is totally defunct in Intrepid 64-bit), xdtv - black screen.

Will accept any piece of advice.

---

### Post by Dedoimedo on 2008-11-20
Not sure if this can help you, but you may want to try MythTV.
It's in the Ubuntu repos, download mythtv and mythtv-plugin.

This is a TiVO-like software, may help you achieve want you want.

More details:
[http://mythtv.org/](http://mythtv.org/)

Dedoimedo

---

### Post by apienk01 on 2008-11-20
Thank you, Dedoimedo. I haven't tried MythTV, but after some more googling and reading I believe now my problems are caused by a bug in em28xx kernel module.

Here's the place to look for Empia tuner driver related problems:
[http://mcentral.de/wiki/index.php5/Main_Page]("http://mcentral.de/wiki/index.php5/Main_Page")

---


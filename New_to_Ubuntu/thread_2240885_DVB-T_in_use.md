---
title: "DVB-T in use"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by Andy_Crowd on 2014-08-22
Hi!
How can I see which program is using DVB-T. When I closing/killing mplayer (while is shows tv) in console then I can get errors about that device is in use and busy next time when I trying to watch tv. Only restart of PC helping.
Just had to use ```
$ ps aux | grep mplayer
``` and followed the [guide]("http://meinit.nl/the-3-most-important-kill-signals-on-the-linux-unix-command-line") about how to kill it, took time didn't die at once, had to use it few times.

---


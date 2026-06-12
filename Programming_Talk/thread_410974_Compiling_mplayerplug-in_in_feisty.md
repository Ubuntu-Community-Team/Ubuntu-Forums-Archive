---
title: "Compiling mplayerplug-in in feisty"
date: 2007-04-16
forum: Programming Talk
---

### Post by jazzgossen on 2007-04-16
I'm tryng to compile mplayerplug-in in Feisty, in order to get it working in Opera. However. it depends on mozilla-dev, which is not available in Feisty, but has been replaced with libnspr-dev. After installing libnspr-dev, the configure script still complains that it can't find the Mozilla development files. What to do?

---

### Post by Colonel Kilkenny on 2007-04-17
I'd suggest trying something else instead of mplayerplugin. Try mozplugger, vlc-plugin, xine-plugin and gecko media player. I'd say your chances are better to get something that actually works.
I'm using Gecko Media Player and it seems to be working okay for all video-files. It needs Gnome Mplayer (compile first Gnome Mplayer and then Gecko Media Player).
[http://dekorte.homeip.net/download/gnome-mplayer/](http://dekorte.homeip.net/download/gnome-mplayer/)

---


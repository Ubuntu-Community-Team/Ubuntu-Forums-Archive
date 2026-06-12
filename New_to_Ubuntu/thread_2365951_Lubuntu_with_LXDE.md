---
title: "Lubuntu with LXDE"
date: 2017-07-12
forum: New to Ubuntu
---

### Post by automate-stuff on 2017-07-12
So Lubuntu is switching to LXQT...Will I still be able to download Lubuntu with LXDE after the switch ? or should I install Ubuntu then manually install the LXDE  ?

---

### Post by vocx on 2017-07-14
> **automate-stuff said:**
> So Lubuntu is switching to LXQT...Will I still be able to download Lubuntu with LXDE after the switch ? or should I install Ubuntu then manually install the LXDE  ?
According to the Wikipedia pages of both LXDE and LXQT, and the sources cited there, it seems LXDE will stop development completely. [https://en.wikipedia.org/wiki/LXDE https://blog.lxde.org/2013/07/22/the-future-of-razor-and-lxde-qt/]("https://en.wikipedia.org/wiki/LXDE")

The author of LXQT is the same as LXDE. He originally started LXDE using GTK+, but later he decided to port the environment to QT, thus creating LXQT.

"This merge means that the Gtk+ [LXDE] and the Qt [LXQT] versions will coexist at first but that, eventually, the GTK version will be dropped and all efforts will be focused on the Qt port[SUP]."[/SUP]

So what this means, is that probably in the future there will be only an LXQT desktop to install. It is possible that LXDE will remain frozen in time in the Ubuntu repositories, so you will probably still be able to install it for some time. But without a proper developer or maintainer, it will simply become obsolete, and probably it will be dropped completely from future versions of Ubuntu.

So it seems the reason Ubuntu is changing to LXQT is not because Ubuntu wants, but simply because the development of LXDE will stop. Unless somebody picks up the LXDE project, I think most people will just transition to LXQT.

---


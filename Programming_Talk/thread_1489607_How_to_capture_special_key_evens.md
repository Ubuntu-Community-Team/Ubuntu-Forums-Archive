---
title: "How to capture special key evens?"
date: 2010-05-21
forum: Programming Talk
---

### Post by cristian.vrabie on 2010-05-21
Hey guys,
Sorry to bother but couldn't find the answer to this by usual googling.
Is it possible for a program (it can be in any language) in Linux (Ubuntu/Gnome if you want to be specific) to capture events of special keys (eg: Fn+VolumeUp)? I was thinking that mapping the keyboard like key loggers do, would be one way, but seems overkill in case of such a limited use. Maybe these events are published somehow/somewhere.
Thanks!
Cristian

---

### Post by soltanis on 2010-05-21
If all you want to do is capture certain keypresses and have them execute certain commands, then you can use a program such as xbindkeys, which will let you bind say your function keys to changing volume, and similar things.

---

### Post by durand on 2010-05-21
Your window manager will also have this functionality. If you use compiz, you can configure it with ccsm. If you use metacity, there is a place in gconf to do it, I think.

---

### Post by cristian.vrabie on 2010-05-22
Ok. Thanks! It's a start. The tricky part to this is that I want to bind actions on these keys IN ADDITION to the system defaults.
My intention with this is to create a browser plugin (Firefox/Chrome) that will capture special keys like (PLAY, STOP, PAUSE, NEXT, PREVIOUS) and pass them to certain web-apps like YouTube Player, grooveshark.com, etc.
I'm used to using these keys with Banshee, Totem, etc. and I think making often used web-apps respond to special keys would be a nice feature.

---

### Post by durand on 2010-05-22
That's a really cool idea! Maybe if you look at a program that does this, you might get an idea of how they do it. Sonata would be a great example. It's written in python so it should be fairly easy to follow. It's in one of these files! [http://git.berlios.de/cgi-bin/gitweb.cgi?p=sonata;a=tree;f=sonata;h=8442112fe4157d2014b5f76506395ca1115de295;hb=HEAD](http://git.berlios.de/cgi-bin/gitweb.cgi?p=sonata;a=tree;f=sonata;h=8442112fe4157d2014b5f76506395ca1115de295;hb=HEAD)

---


---
title: "show now playing song"
date: 2006-03-24
forum: Programming Talk
---

### Post by hezral on 2006-03-24
hi.i was wondering if there is a program that can do this? 

i used to use it when i had my powerbook.
if there's no such app, is it hard to program? i dont really know much about programming tho..

---

### Post by Wolki on 2006-03-24
Depends on what muisc player you're using. Many already have OSD or notify support either built-in or as a plugin, for others it can be done rather easily if you know how, yet others might be difficult.

---

### Post by hezral on 2006-03-24
well i was thinking doing exactly the same as in the sshot. probably for rhythmbox or banshee.

---

### Post by Wolki on 2006-03-24
You could probably use xosd for a similar effect. I'm not too familiar with it, iirc it defaults to green but you should be able to change that. The xmms-like players often have plugins for this, There's a plugin in the works for banshee ([http://blog.heatxsink.com/archives/2006/02/xosd_plugin_par.html](http://blog.heatxsink.com/archives/2006/02/xosd_plugin_par.html)) but i don't know if that works well.

There are python bindings for xosd, if your player exports its information e.g. via dbus, you should be able to write a quick script that does a similar effect. Not sure you can do the background, though-

---


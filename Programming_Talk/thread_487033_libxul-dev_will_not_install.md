---
title: "libxul-dev will not install"
date: 2007-06-28
forum: Programming Talk
---

### Post by Triscuit713 on 2007-06-28
I would like to write a moonlight (the novell implementation of silverlight) widget. One of moonlight's dependencies is libxul, as stated here:

[http://www.mono-project.com/Moonlight]("http://www.mono-project.com/Moonlight")

The debian build method is here:
[http://groups.google.com/group/mono-olive/browse_thread/thread/7706c2dac175d4f6]("http://groups.google.com/group/mono-olive/browse_thread/thread/7706c2dac175d4f6")

However, libxul-dev won't install, and this is apparently a known bug. I need libxul-dev to satisfy the Mozilla XPCOM dependency.

 How can I circumvent this?

---

### Post by duff on 2007-06-28
what about firefox-dev?

---

### Post by Strung on 2007-08-13
Hi ,

I would like to rebuild package mozilla-mplayer to enable option --enable-x in compilation (required to have mplayerplug-in with opera). I have dependencies with libxul-dev to satisfy but synaptic can't resolve thems. 

libxul-dev:
 Dépend*: libnss3-dev mais ne doit pas être installé
 Dépend*: libnspr4-dev mais ne doit pas être installé
 Dépend*: libmozjs-dev mais ne doit pas être installé

(mais ne doit pas être installé=but must not be installed)

How can i resolve this issue because i can't rebuild package? I am not sure that firefox-dev is the good solution. 

Thanks for your help.

---


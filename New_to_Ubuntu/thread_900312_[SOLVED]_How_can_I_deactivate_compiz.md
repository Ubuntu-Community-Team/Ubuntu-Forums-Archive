---
title: "[SOLVED] How can I deactivate compiz?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sdim on 2008-08-25
Hi,everyone.
Just installed Mint Elyssa,which is based on Hardy,and because I have problems watching movies ("tearing" effect),I would like to deactivate Compiz,since doing so in Daryna seemed to work.
Many thanks.

---

### Post by wgrant on 2008-08-25
> **sdim said:**
> Hi,everyone.
Just installed Mint Elyssa,which is based on Hardy,and because I have problems watching movies ("tearing" effect),I would like to deactivate Compiz,since doing so in Daryna seemed to work.
Many thanks.

You likely want System->Preferences->Appearance->Visual Effects. You can then select 'None'.

---

### Post by sdim on 2008-08-25
That's it.Thanks for reminding me.

---

### Post by 3rdalbum on 2008-08-25
There's another way of doing it, which is handy for using in scripts (if you've got a program that doesn't play nice with Compiz, but you don't want it turned off perminantly).

```
metacity --replace
```

Starts the regular Gnome window manager. If you want to start Compiz again:

```
compiz --replace
```

If, for instance, you need Compiz turned off in order to run Kdenlive, here's what you'd put in the script:

```

#!/bin/sh

metacity --replace &
sleep 1
kdenlive
compiz --replace

```

Make the script executable, double-click it and you'll switch back to the Metacity window manager, wait 1 second for the change to happen, and start Kdenlive. When Kdenlive quits or crashes, Compiz starts back up.

---

### Post by ajgreeny on 2008-08-25
Or if you go to forlong's site you can get hold of compiz-switch which is a simple script file installer and allows you to turn compiz on and off at will.  Go [here]("http://forlong.blogage.de/article/pages/Compiz-Switch").

---

### Post by Paqman on 2008-08-25
There's also a [Compiz icon](apt:fusion-icon) (click to install) that you can have sit in a panel if you want something on your desktop for switching between Compiz and Metacity. It's in the Universe repo.

---

### Post by sdim on 2008-08-26
Many thanks to all of you.

---

### Post by -Zeus- on 2008-08-26
> **3rdalbum said:**
> There's another way of doing it, which is handy for using in scripts (if you've got a program that doesn't play nice with Compiz, but you don't want it turned off perminantly).

```
metacity --replace
```

Starts the regular Gnome window manager. If you want to start Compiz again:

```
compiz --replace
```

If, for instance, you need Compiz turned off in order to run Kdenlive, here's what you'd put in the script:

```

#!/bin/sh

metacity --replace &
sleep 1
kdenlive
compiz --replace

```

Make the script executable, double-click it and you'll switch back to the Metacity window manager, wait 1 second for the change to happen, and start Kdenlive. When Kdenlive quits or crashes, Compiz starts back up.

you'd be better off using compiz --replace& in the script... unless you want that script running until next reboot

---

### Post by Tom--d on 2008-08-26
You know you can change the video display in compiz. Basically have compiz+video. its simple.

ALT+F2 then type in
```
gstreamer-properties
```
and go to the video tab and change the DEfault output to
**X Window System (No XV)**
and now you can have all the effects with video.
This only applies to gstreamer back end.
If its xine... I dont know where to look. (it can be done).

---

### Post by sdim on 2008-08-27
Thanks,Tom--d.Does that mean that I will be able to watch video without the "tearing" effect?

---


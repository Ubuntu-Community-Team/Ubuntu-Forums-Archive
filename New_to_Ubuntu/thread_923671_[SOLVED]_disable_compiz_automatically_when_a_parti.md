---
title: "[SOLVED] disable compiz automatically when a particular application is running?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-09-18
Is it possible to automatically disable Compiz-Fusion when I run XBMC? and then have it automatically switch back when I exit XBMC?

Thanks in advance:KS

---

### Post by northern lights on 2008-09-18
As for the opening part, you could create a custom launcher somewheres and as the 'command' entry put```
metacity --replace && *xbmc*
```or whatever launches *the media center*(never used it)

---

### Post by kamitsukai on 2008-09-18
> **northern lights said:**
> As for the opening part, you could create a custom launcher somewheres and as the 'command' entry put```
metacity --replace && *xbmc*
```or whatever launches *the media center*(never used it)

I'm afraid that didn't work...properly? it went back to metacity but it didn't load xbmc...so I selected compiz from "compiz-fusion icon" and then xbmc loaded:confused:

Slightly weired

---

### Post by northern lights on 2008-09-18
> **kamitsukai said:**
> it went back to metacity but it didn't load xbmcI sort of expected that to happen if the suggested was run verbose. Thus the following comment:
> **northern lights said:**
> or whatever launches *the media center*...

---

### Post by madsmeg on 2008-09-18
I have a script i run on my desktop when i want to run somthing without Compiz 

```
#! /bin/bash
pid=`ps --no-heading -C compiz.real | cut -d "?" -f1`;
if [ -n "$pid" ]; then
metacity --replace
else
compiz --replace
fi
```

It detects if compiz is running, if it is it turns it off, if its not it turs it on

Hope this helps

---

### Post by cbreaker on 2009-10-28
Madsmeg, thanks for your simple script.   It ain't perfect but it will do, thanks a bunch.

Notice that the Ubuntu devs have a note about this one that says "Well, this will be fixed with DRI2 and only Intel has support for that.. Who knows about nVidia or ATI.. Sorry."

In other words, they won't help create a tool that will do this for specific apps since the "solution" is a fundamental new feature of the video drivers?

Sometimes Microsoft gets it right, and with Vista's compositing engine they included the ability to automatically disable Glass when an incompatible app was detected.

So, the answer is simple!   Wait until the cows come home or write our own utility?   Sweet~

---


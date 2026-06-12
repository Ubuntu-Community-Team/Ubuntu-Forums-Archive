---
title: "2 issues"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
Well, one issue and one nuisance, heh.
Occasionally, when i close firefox (i have firefox3rc), when i try to open it again, it just says "starting firefox" at the bottom of my screen for like 5 seconds and goes away. and firefox doesn't open.

my nuisance is that i downloaded Audcaious, and i cant minimize it to the tray by the clock. I tried AllTray, but it doesn't work. is there a plugin or anything to do it?

---

### Post by Inxsible on 2008-05-27
FF3RC is a little buggy in that it does that sometimes. I had my plugins' preferences all screwed up eg Ctrl + number opened that webpage  from speed dial and now Ctrl + number only selects that tab and i havent been able to change it either.

So anyway, try purging your system and then re-installing the RC
```
sudo aptitude purge firefox
```No idea about Audacious - never used it.

I would like you to have a look at cplay - a command line music player which if used under screen does not even show on the desktop. So its always out of the way - but still playing music

---

### Post by Tux Aubrey on 2008-05-27
> Occasionally, when i close firefox (i have firefox3rc), when i try to open it again, it just says "starting firefox" at the bottom of my screen for like 5 seconds and goes away. and firefox doesn't open.


I don't know a permanent fix, but if its not opening properly I find that if I click on another Virtual Desktop in the pager it will usually open on that new desktop. Worth a try.

---

### Post by adobrakic on 2008-05-27
Thanks guys, ill try both.
Anyone know anything about the audacious issue?

also, what does purging firefox exactly do?

---

### Post by Inxsible on 2008-05-27
> **adobrakic said:**
> Thanks guys, ill try both.
Anyone know anything about the audacious issue?

also, what does purging firefox exactly do?Purging removes the application as well as the user properties for that app. That way you get a clean slate to install the same program again.

---


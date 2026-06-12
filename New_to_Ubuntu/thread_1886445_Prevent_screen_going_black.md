---
title: "Prevent screen going black"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by Andalado on 2011-11-24
Hi everyone i am a user or lubuntu since 10.04 and now am using 11.10. I always love how light it is. but there's one thing that i don't like and it's that the screen goes black after a few minutes. I hate that because i want my screen to be always on (contrary to the lubuntu mantra 'energy-efficient') i already went to xscreensaver settings an disable the screensaver and nothing happend, then a went to the power settings an put on the screen tab never to blackout and the situation continues. i need help please.
p.s. sorry about my english

---

### Post by gatgat23 on 2011-11-24
What about using caffeine?

---

### Post by Andalado on 2011-11-25
I thought about using caffeine, but i prefer a local solution

---

### Post by Rodney9 on 2011-11-25
I am using Lubuntu 11.10 on my laptop, I disabled screensaver and power management , now my screen is always on.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Heme on 2012-02-11
> **Rodney9 said:**
> I am using Lubuntu 11.10 on my laptop, I disabled screensaver and power management , now my screen is always on.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

Sorry to bump an old thread, but I have pretty much the same problem as the thread starter. I've lubuntu on my netbook and use it mainly to monitor im's and such, so I'd like it to stay on. I disabled screensaver and power management from the window but it still keeps going dark after 10mins of inactivity which is annoying.

I tried browsing that general guide, but it's quite daunting with those couple hundred entries and only thing I found with searching it was a link to thread that only solved the issue with media player on.

Did I miss something obvious?

(love lubuntu btw, great for netbook)

Edit: Okay, I killed the daemon in the screensaver window and that seems to have done it. I seem to continue my embarrassing habit of finding out the solution at random right after making a post about it.

---

### Post by Andalado on 2012-02-12
Hi, i have found the solution, all you have to do is open the file /etc/xdg/lxsession/Lubuntu/autostart and add these lines (with superuser privileges)

```
@xset dpms 0 0 0
@xset -dpms
@xset s noblank
@xset s off
```

and that's it no more screen going black

---


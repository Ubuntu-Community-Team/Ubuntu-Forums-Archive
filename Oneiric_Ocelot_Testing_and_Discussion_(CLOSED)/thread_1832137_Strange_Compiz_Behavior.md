---
title: "Strange Compiz Behavior?"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-24
Is anyone else seeing compiz pegged at 30% of the CPU?

---

### Post by ventrical on 2011-08-24
I got 11 to 20 and I have been online for about 2 hours now.

---

### Post by arpanaut on 2011-08-24
Mine sits @ 22% cpu
6% mem which sometimes increases gradually with long up-time
I don't see any performance degradation though.

---

### Post by ventrical on 2011-08-24
> **arpanaut said:**
> Mine sits @ 22% cpu
6% mem which sometimes increases gradually with long up-time
I don't see any performance degradation though.


Agreed .. no degradation in performance.

---

### Post by mc4man on 2011-08-24
> **moore.bryan said:**
> Is anyone else seeing compiz pegged at 30% of the CPU?

Every once and a while - normally if not doing anything compiz uses 0% cpu 
In all cases here when compiz gets 'stuck' using 15-30%cpu it has come after a compiz crash (may be seen sometimes as a nautilus crash
In many instances the crash may not be noticed or missed.

I'd clear your /var/crash folder and then ck. every once and a while (I clear mine a couple of times a day and always before shutdown and have /var/crash bookmarked
```
sudo rm /var/crash/*.crash
```

---

### Post by budluva04 on 2011-08-24
im sitting at about %30 right now, system seems very usable, clearing all my crash reports did help quite a bit...

---

### Post by moore.bryan on 2011-08-24
I also don't really see any significant performance hits; however, my fan kicks-up itself a bit more with the higher CPU usage and that worries me a bit. I know, I know... that's what the fan is supposed to do. It's just I've had past bad experiences with fans...

---

### Post by mc4man on 2011-08-24
> **moore.bryan said:**
> I also don't really see any significant performance hits; however, my fan kicks-up itself a bit more with the higher CPU usage and that worries me a bit. I know, I know... that's what the fan is supposed to do. It's just I've had past bad experiences with fans...

Generally any app that's using 15 - 30% cpu on a single thread isn't going to cause a 'performance' hit, not really the point. Compiz shouldn't be using any cpu unless you're doing something related.

If you were to log out/in and it;s still doing so then I'd ck. for recent compiz crash, if none then file a bug on compiz.
If you have an install that's fairly old I'd consider a fresh one.
screen shows typical here - no cpu use for compiz

(just noticed the new version of gnome-screenshot is butchering names quite nicely

---

### Post by moore.bryan on 2011-08-24
Yeah... I'm not really doing anything and it's pegged at no less than 25% and maxes to about 60% every now and again.

---


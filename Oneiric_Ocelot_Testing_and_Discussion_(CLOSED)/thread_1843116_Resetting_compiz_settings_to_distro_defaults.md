---
title: "Resetting compiz settings to distro defaults?"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-12
I've been playing around with compiz plugins settings and applying regexps for specific rules, etc in order to make the desktop more usable despite the window focus problems (which still haunt me even after todays upgrades to compiz and unity).

Is there a proper way to reset compiz and its plugins to the distribution defaults? I imagine that if I just purge and reinstall it I probably won't be having them set the way compiz / unity developers expect users to have them configured as of now (considering workarounds, etc).

Regards,
Effenberg

---

### Post by mc4man on 2011-09-12
'Probably' 
```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by drs305 on 2011-09-12
If you have installed the CompizConfig Settings Manager (ccsm) you should be able to reset to the compiz defaults via the Preferences, Profile button.

---

### Post by jbicha on 2011-09-12
You should be able to just run

```
unity --reset
```

---

### Post by effenberg0x0 on 2011-09-13
Excellent solutions, its fixed. It's funny I had never seen the profile option inside CCSM and was doing things in a much more complicated way (get/set with gconftool inside bash script).

Anyway, its all fixed now.

Thanks,
Effenberg

---

### Post by drs305 on 2011-09-13
> **effenberg0x0 said:**
> EIt's funny I had never seen the profile option inside CCSM and was doing things in a much more complicated way (get/set with gconftool inside bash script).

As you can probably guess, it's also a very simple way of backing up your compiz customizations once you get things set up the way you want them.

Happy Ubuntu-ing !

---


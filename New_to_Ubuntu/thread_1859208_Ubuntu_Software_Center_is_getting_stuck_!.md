---
title: "Ubuntu Software Center is getting stuck !"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by perito on 2011-10-13
how can I see more details when the new Ubuntu Software center is installing something ? its getting stuck installing Adobe Flash Plugin ("Applying Changed") I waited for 1 hour 30 minutes without anything happening !

---

### Post by perito on 2011-10-13
its actually getting stuck on all "Applying Changes" !!

---

### Post by elessar9 on 2011-10-13
Something similar happened to me. I ran synaptic, which told me to run a dpkg command in terminal (sudo dpkg --configure -a). This completed the flash plugin install, and everything is now working smoothly

---

### Post by kaldor on 2011-10-13
This is happening to me right now. I was installing the *ubuntu-restricted-extras* package, and after accepting a license, it's been stuck on "applying changes" for the last 15 minutes with the bar 3/4 of the way done.

Edit: found this when I ran *ps ax*

```
30492 ?        Z      0:00 [flashplugin-dow] <defunct>

```

---


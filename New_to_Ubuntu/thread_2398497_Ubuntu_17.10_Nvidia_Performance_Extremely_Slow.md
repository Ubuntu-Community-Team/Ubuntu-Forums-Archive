---
title: "Ubuntu 17.10 Nvidia Performance Extremely Slow"
date: 2018-08-13
forum: New to Ubuntu
---

### Post by marthalroy on 2018-08-13
[COLOR=#000000]I'm running Ubuntu 17.10 on my Intel graphics laptop and my Radeon rigs with great success, but on my main desktop with Nvidia graphics Gnome runs terribly. Gnome 3.26 seems faster than Gnome 3.24 and 3.24 used to run ok ish on this rig but now not so. Is anyone else experiencing sluggishness and major stuttering with animations on Nvidia graphics? Thanks.[/COLOR]

---

### Post by kc1di on 2018-08-13
Which driver are you using for the nvidia card?
If not sure run this command from a terminal and post the results.```
lspci -vnn | grep VGA -A 12
```

---

### Post by Impavidus on 2018-08-13
Ubuntu 17.10 is dead. It reached end of life a few weeks back. I suggest you upgrade to or fresh install 18.04.

---

### Post by Autodave on 2018-08-13
+1 with Impavidus.  Let's start with a new, supported version: 18.04.  Chances are that the proper Nvidia driver will be installed automatically, but to make sure:  After installing 18.04 and any/all updates, go to Additional Drivers.  If there is a recommended one there, install it.  Then come back and let us know how it is running.  If there is still a problem, please tell us what Nvidia card is in the machine and what driver is installed.

---


---
title: "[SOLVED] Getting Ubuntu/Gnome without all the apps"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by snowpine on 2008-06-10
Let's say I already have the Hardy base system installed with a different windows manager (Fluxbox in my case, but it could be xubuntu or kubuntu etc). Now I want to experience the joys of the gnome ubuntu desktop, with all the menus, panels, etc. but none of the software applications. If I apt-get install ubuntu-desktop, I get the whole "suite." How do I just install the basics to run an ubuntu-flavored gnome session?

For example, I once tried adding kubuntu-desktop. Big mistake; it added a whole new set of k-themed apps to clutter up my system and menus!

---

### Post by aysiu on 2008-06-10
```
sudo apt-get install gnome-core
```

---

### Post by snowpine on 2008-06-10
> **aysiu said:**
> ```
sudo apt-get install gnome-core
```

Thank you Aysiu for the quick reply! I will give that a try. I could then add the themes with 'ubuntu-artwork', right?

---

### Post by aysiu on 2008-06-10
> **snowpine said:**
> Thank you Aysiu for the quick reply! I will give that a try. I could then add the themes with 'ubuntu-artwork', right?
Or *gnome-themes* or *gnome-theme-extras*

---


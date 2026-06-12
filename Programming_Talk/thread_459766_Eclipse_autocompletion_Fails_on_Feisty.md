---
title: "Eclipse autocompletion Fails on Feisty"
date: 2007-05-31
forum: Programming Talk
---

### Post by aitalaat on 2007-05-31
Hi,
Just switched to Feisty. Installed Sun Java6 + eclipse and edited /etc/eclipse/java_home

All went well the first time. But then autocompletion doesn't work anymore. I downloaded the .tar file from the site and still the same problem.

Any Suggestions??

---

### Post by gnirts on 2007-06-18
Ctrl + Space works to autocomplete for me, 7.04 and Eclipse 3.2.2 (Linux GTK version). What perspective are you in? Are you using any plugins? Do you have Desktop Effects (System > Preferences > Desktop Effects) enable?

---

### Post by aitalaat on 2007-06-18
Actually i was able to find the problem. It's Scim. Cause i have arabic enabled so scim filters my keyboard strokes before it passes it to eclipse. And scim had some shortcuts of its own like Ctrl + Space. So i just disabled it

---


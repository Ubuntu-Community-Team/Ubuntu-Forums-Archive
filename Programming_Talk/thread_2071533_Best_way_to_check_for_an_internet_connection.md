---
title: "Best way to check for an internet connection"
date: 2012-10-15
forum: Programming Talk
---

### Post by lykwydchykyn on 2012-10-15
I'm working on a login script to delay the launch of a program until after the wireless connection (via nm-applet) is setup.  My initial thought is to repeatedly grep the output of ifconfig until an ip address can be found, but this seems messy and maybe prone to error.

Does anyone have any advice on a better approach to this task?

---

### Post by trent.josephsen on 2012-10-15
[nm-online](http://linux.die.net/man/1/nm-online)?

---

### Post by lykwydchykyn on 2012-10-15
Didn't know that existed; thanks, I will try it!

---


---
title: "run console command upon logging into lubuntu X environment"
date: 2014-09-15
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-09-15
Hi all, 

I'd like to run two console commands upon each time I log into lubuntu X environment: 

xset s off
xset -dpms

How do I perform it?

---

### Post by TheFu on 2014-09-15
Drop them into:
   ~/.config/openbox/autostart

Might need the full path to each command - xset is  ... /usr/bin/xset - that's always a good idea for scripts.
This assumes you are running openbox (the default under lxde)

---


---
title: "[SOLVED] Missing Suspend Icon"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by dse.37 on 2008-11-14
This is more of an annoyance than a problem, but I'd like it sorted anyway.

I've noticed that after installing Intrepid that the suspend icon is missing from the shutdown dialogue when using certain icon themes. It's there when I use the Human icon theme (just looked), but I'm using gperfection2 and would like to keep it that way.

Can anybody shed some light on how I can fix this problem?

Thanks in advance.

---

### Post by dse.37 on 2008-11-14
Sorry, I got it.
I had a look in /usr/share/icons/Human/(48x48/actions/sleep.png) to see where the suspend icon should have been and simply made what changes I needed to in the /gperfection2/48x48 directory.
Created a folder called actions and placed the sleep.png inside.

;D

---


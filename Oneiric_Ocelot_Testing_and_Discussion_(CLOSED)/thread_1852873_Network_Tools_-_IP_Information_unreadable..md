---
title: "Network Tools - IP Information unreadable."
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-10-01
I couldn't find this mentioned before. Have a look at my screenshot, under "IP Information". Anyone else seeing this?

There's a scroll bar for the orange bit if I hover the mouse in the right area, but it doesn't help to make the information visible. I can't see if there is any way to enlarge the information area. Originally installed from Beta1, and now fully up-to-date. This is the first time I've opened Network Tools. 

If I choose lo from the drop-down, same story.

---

### Post by alphacrucis2 on 2011-10-01
Same here. The scroll buttons pop up for me but the vertical space is too small to read what is being displayed. My install is updated from 11.04.

---

### Post by lucazade on 2011-10-01
the same issue is present also in dconf-editor.. I usually workaround by clicking one time then using arrow keys.. this way the list becomes fully visible.
I suppose it is an issue in gtk3 listview widget.. so something upstream.

---

### Post by coffeecat on 2011-10-01
Unfortunately, the arrow keys don't work any better than the scroll-bar to make it visible - at least not for me in Network Tools. I'm sure you're right about it being an upstream issue. I'll have a rummage around in Launchpad and see if I can find anything.

**EDIT**: I've found this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/856387](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/856387)

I've done me-too. I'll see if there are any others.

---


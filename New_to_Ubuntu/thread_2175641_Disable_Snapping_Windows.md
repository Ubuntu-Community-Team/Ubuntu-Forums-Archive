---
title: "Disable Snapping Windows"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-09-20
I want to disable the windows from going full screen when i drag them up to the top bar.
Thanks in advance.

---

### Post by grainbarcelona on 2013-09-20
Open the CompizConfig Setting manager (install it from the software centre first, if you haven't installed it)
Unclick 'Snapping Windows' in the Windows management settings. Check out the other options there as well.
The details depend on which version of ubuntu you're using

---

### Post by stinkeye on 2013-09-20
**grainbarcelona** is on the right track except I think what your looking for is the grid plugin.

Install ccsm.
In terminal....
```
sudo apt-get install compizconfig-settings-manager
```

To run, enter ccsm in the dash.

Go to ccsm > window management > grid > edges > resize actions
and disable the top edge entry.

---

### Post by Danny_Michel on 2013-09-21
thanks

---


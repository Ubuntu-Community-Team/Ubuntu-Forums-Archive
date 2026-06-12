---
title: "Strange bug. Happens to you too?"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2011-09-21
In unity - If I minimize (i.e. the **-** icon) a **maximized** window, I can't control any windows or desktop items that were beneath it. It's as if the maximized window that I minimized is still there when it's not. I have to maximize it again and then to un-max it to fix it, or to push it to another workspace before I can use other windows or desktop items.

---

### Post by papibe on 2011-09-21
> I just tried that with Firefox and the problems doesn't seem to appear.

Does it happen with any application?

Regards.

Please ignore my comment, I tried this on Natty

---

### Post by mc4man on 2011-09-21
Will be fixed in the next day or so with the next compiz upgrade
(have tested  the new packages and all be be back to normal

There is a workaround, -  though after compiz upgrades you'd want to undo it or there could be some new related window issues 

So you  could just wait for new compiz & avoid minimizing windows in the meantime or run this command
```
gconftool-2 -s -t boolean /apps/compiz-1/plugins/unityshell/screen0/options/show_minimized_windows false

```
then log out/in
After compiz upgrades then revert w/
```
gconftool-2 -s -t boolean /apps/compiz-1/plugins/unityshell/screen0/options/show_minimized_windows true
```
log out/in

---


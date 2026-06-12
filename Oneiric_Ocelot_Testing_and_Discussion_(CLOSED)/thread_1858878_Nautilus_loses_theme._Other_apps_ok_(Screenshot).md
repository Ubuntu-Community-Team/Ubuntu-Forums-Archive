---
title: "Nautilus loses theme. Other apps ok (Screenshot)"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-13
This had happened to me before, but I didn't report it cause I thought it was my fault. 

Today, while copying a large file over SMB, Nautilus suddenly redraw with no theme. 

Closing all Nautilus windows / Reopening them makes no effect. 

See screenshot. All windows have the Ambiance theme, except for Nautilus...

I don't know if it makes any sense to report it now anyway.

Regards,
Effenberg

---

### Post by soro2005 on 2011-10-13
I think it happens sometimes when compiz crashes/reloads. Since Nautilus keeps running in the background, it just loses the theming to never get it back. You can generally fix it by killing the Nautilus processes. Like this in a terminal window (or in the command prompt that you can get up with Alt+F2)
```
nautilus -q
```

---

### Post by lucazade on 2011-10-13
It looks like gnome-settings-daemon died and your session fallbacks to "stock" settings.

This happens also in the old natty gtk2 environment and it is due to indicator patches of g-s-d (especially xrandr.patch).
G-s-d used in gdm is still alive after the desktop is completely loaded and conflicts with g-d-m of the session in use. A catch22 and really hard to fix also for our great Gnome hacker Rodrigo Moya (personally I've spent a lot of hours trying to help him with some testing).

A couple of days ago seb128 asked if the bug is present also in Oneiric, personally i've never seen in these 6 months.. lightdm is employing indicators so it could potentially lead to this problem.

If you want to report it I suggest you to use this bug report.
[https://bugs.launchpad.net/ubuntu/natty/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/natty/+source/gnome-settings-daemon/+bug/649809)

---

### Post by wetch on 2011-10-13
Same thing had me scratching my head too. Thanks for the tip to restart Nautilus...

---


---
title: "Dapper top and bottom panels disappeared"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Skimbleshanks on 2008-09-06
It all started when I started the screensaver, probably because the RAM is very limited on my computer. The screen changed to vertical lines so I was working blind from there on.
After turning off the computer and restarting the menu bar at the top (by default) of the screen, and the workspace bar at the bottom (by default) had disappeared. I think I saw something about a shortcut to turn them on/off but haven't been able to find it.

Help!

---

### Post by alienexplorers on 2008-09-07
Try this command from terminal:
> sudo apt-get install gnome-panel

---

### Post by Oldsoldier2003 on 2008-09-07
> **Skimbleshanks said:**
> It all started when I started the screensaver, probably because the RAM is very limited on my computer. The screen changed to vertical lines so I was working blind from there on.
After turning off the computer and restarting the menu bar at the top (by default) of the screen, and the workspace bar at the bottom (by default) had disappeared. I think I saw something about a shortcut to turn them on/off but haven't been able to find it.

Help!

from a terminal:
```
gnome-panel
```

you can press alt+F2 and type gnome-terminal to start a terminal. or you could right click the desktop and create a launcher if alt+F2 doesn't work for you.

---

### Post by Skimbleshanks on 2008-09-07
> **alienexplorers said:**
> Try this command from terminal:

The result was:
Package gnome-panel is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted or is only available from another source.

Can somebody very patient please walk me through the steps to reinstall gnome-panel?

And equally important, are there any clues in my messages so far to indicate why/how it was deleted?

---

### Post by Skimbleshanks on 2008-09-10
Thank you, everybody who offered advice.
In the end I remedied the problem by simply reinstalling.
[CENTER]:)[/CENTER]

---

### Post by Skimbleshanks on 2008-09-10
Something I found while looking for something else entirely:
Alt+F2 (as previously recommended)
xfce4-panel

---


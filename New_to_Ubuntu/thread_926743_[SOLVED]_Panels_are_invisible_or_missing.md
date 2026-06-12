---
title: "[SOLVED] Panels are invisible or missing"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by mhedges48 on 2008-09-22
Hello, my panels have disappeared. I have tried
apt-get --reinstall install ubuntu-desktop
as well as purging gnome-panel and reinstalling, etc., with no luck... when I try and run gnome-panel from the terminal, it says "A panel is already running".

I hit the windows start key on the keyboard and it brings up an EMPTY box for the main menu...

I used to have two panels, one on the bottom left corner and the other on the bottom right (with AWN in the middle). Now I just have AWN and not panels... any ideas on how to get them back?


thanks!

---

### Post by ThrobbingBrain66 on 2008-09-22
Is it possible you accidentally hid the panels using compiz? Hit Alt+F2 and a Run Application box should pop up.  Type the following into that box:
```
metacity --replace
```

---

### Post by mhedges48 on 2008-09-22
Tried that (thanks) but no luck... it disabled compiz when I ran it, but panels did not reappear...

---

### Post by aeiah on 2008-09-22
if ```
killall gnome-panel
``` does not work (which it probably wont)

you could try looking at the panel config or removing the panel config file, or going into gconf-editor

[http://mailman.lug.org.uk/pipermail/nottingham/2006-April/007909.html](http://mailman.lug.org.uk/pipermail/nottingham/2006-April/007909.html)

---

### Post by mhedges48 on 2008-09-22
Thanks! That fixed it. The problem was the gconf settings (they remained even after purging/deleting gnome-panel and reinstalling). 

It was fixed by:
apt-get remove gnome-panel
Deleted the panel directory from .gconf
apt-get --reinstall install ubuntu-desktop

---

### Post by mailtwogopal on 2008-09-22
Hi guy,

  Mark this thread as solved please.

---


---
title: "updates ruined Gnome login"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-08-24
I just updated today after being away from the computer for 2 weeks. There were 45 new updates mostly for xine and vlc and evolution plus a couple of extra updates from addons I made to my sources.list file (sorry I can't post it since I can't login; I can describe the updates though). They were for cinelerra and cdemu and at least one other that I can't remember.

Importantly when I start up my computer and it gets to the gnome login program it loads the default login style (which I set it at) which stays on the screen for about 1 second and then it reloads the same window (can't type in the username box nor click on the options tab). I remember that after I updated and tried to run any programs that it would not load but I could click on the shut down button on the panel (so I restarted to try and fix it and got to this problem).

Does anyone know how I could login so I could try and fix this problem? Or perhaps has this happened to anyone else?

---

### Post by Kizlum on 2008-08-24
Have you got access to tty1? (try to press Ctrl+Alt+F1 when you are on the login screen).

---

### Post by fontenot_1031 on 2008-08-24
> **Kizlum said:**
> Have you got access to tty1? (try to press Ctrl+Alt+F1 when you are on the login screen).

WOOO YEAH!
Ok that worked. Now I need to figure out how to fix the Gnome login program.

Now is there a log file that tracks the most recent updates that I made with apt-get update?

Btw, I just found out that the other two addons for sources.list were wxpython (no new updates) and exaile (no new updates). So only cinelerra was updated.

---


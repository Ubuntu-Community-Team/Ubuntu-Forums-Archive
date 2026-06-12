---
title: "compiz"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-23
i am using KDE 4.1 on ubuntu hardy,that has gnome as the default desktop environment.i have all the eye candy running on gnome,i.e,emerald themes,compiz fusion,and many other things.but,when i log on to a KDE 4 session,i can't use compiz,and also beryl and GTK themes,though they do appear as programs and i can even configure them.how can i use them?i mean only emerald themes give me transparent window borders which i can't live without.

---

### Post by ggaaron on 2008-08-23
To use compiz run 'compiz --replace'. You can also go to System Settings -> Session Manager and change window manager there.

---

### Post by stonecoldjha on 2008-08-23
how can i do this?

---

### Post by ggaaron on 2008-08-23
Alt+F2 and then run compiz --replace, possibly you'll have to run emerald --replace too. But setting compiz in KDE system settings seems like a better idea - persistent across sessions and so on.

---

### Post by stmiller on 2008-08-23
KDE4 has its own desktop effects built in. Go to 

System Settings> Desktop > Enable Desktop Effects

---

### Post by ggaaron on 2008-08-23
> **stmiller said:**
> KDE4 has its own desktop effects built in. Go to 

System Settings> Desktop > Enable Desktop Effects

kWin has a limited set of effects. I don't say it's bad, I'm using it right now, but in compositing support it can't stand compiz.

---

### Post by SunnyRabbiera on 2008-08-23
actually there is a way to change this, if you go into the system settings and go to sessions/ session manager or whatever its called (I think its in the first tab, I dont like KDE4 so I dont use it that often)
from there you can change KDE to start up with compiz, it has a pulldown menu in it to change things.

---

### Post by eightmillion on 2008-08-23
On your kmenu go to **System>System Settings**. Click the advanced tab. You should see the first window. Click on Session Manager and change the Window Manager section to Compiz.

---

### Post by SunnyRabbiera on 2008-08-23
> **eightmillion said:**
> On your kmenu go to **System>System Settings**. Click the advanced tab. You should see the first window. Click on Session Manager and change the Window Manager section to Compiz.

yeh that is what I was talking about, like I said I dont use KDE4 that often (only for testing)

---

### Post by stonecoldjha on 2008-09-05
ok thanks,i could get it done as you told.but,now i can't switch to the default KDE window manager from compiz despite setting it up in the sessions manager in sysytem settings.i would like to play around with pure KDE and its desktop environment,so how do i switch to the default KDE window manager.

---

### Post by ggaaron on 2008-09-05
'kwin --replace' will give you kwin as desktop manager.

---


---
title: "How to set icon for application"
date: 2010-12-17
forum: Programming Talk
---

### Post by mecrazycoder on 2010-12-17
Hi,
   I have developed an application using QT creator. Now I like to assign an icon to that application. After going through few many sites, I came cross this site [http://www.freedesktop.org/wiki/Howto_desktop_files](http://www.freedesktop.org/wiki/Howto_desktop_files). But I cant understand and make it run. So can anyone please let me know how to integrate an application with desktop environment.

---

### Post by roccivic on 2010-12-17
Placing icons inside the application is a Windows kind of a thing to do.
You should just save your icon as a PNG (or XPM) image and place it into the /usr/share/icons/ directory.
Then it will be available to you when creating shortcuts.

---

### Post by mecrazycoder on 2010-12-17
> **roccivic said:**
> Placing icons inside the application is a Windows kind of a thing to do.
You should just save your icon as a PNG (or XPM) image and place it into the /usr/share/icons/ directory.
Then it will be available to you when creating shortcuts.
Tanx for ur response. So if i want to run the executable in some other sys, then also i need to place the icon in that folder rite?

---

### Post by roccivic on 2010-12-17
Well, that's the default folder. If you place you icon there, you can access it without specifying the full path.

/usr/share/pixmaps is also still being used, not sure about the details though.

---


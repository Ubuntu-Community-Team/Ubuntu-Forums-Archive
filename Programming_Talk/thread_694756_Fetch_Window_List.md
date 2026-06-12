---
title: "Fetch Window List"
date: 2008-02-12
forum: Programming Talk
---

### Post by mmxbass on 2008-02-12
I am thinking about developing a replacement for the gnome taskbar in the form of either a desklet or a normal GTK+ application.

My question is this: Where is the API that I can query to get information on the currently running applications so that I can populate my widget? The gpanel taskbar is getting the information from SOMEWHERE clearly so. What do I need to call to get the information?

---

### Post by stroyan on 2008-02-12
The gnome window list applet in the gnome panel uses libwnck to list tasks.
Use 'sudo apt-get install libwnck-dev' and browse to
file:///usr/share/doc/libwnck-dev/html/libwnck/index.html
to see documentation of the library.

You can get the actual source for the panel window list applet with this-
apt-get source gnome-panel
You can see the most interesting source in here-
view gnome-panel-2.20.1/applets/wncklet/window-list.c

You can also get the source for the libwnck library-
apt-get source libwnck
The source making xlib calls to get the task information is in here-
view libwnck-2.20.1/libwnck/screen.c

---

### Post by Keith Hedger on 2008-02-12
I would also install dev-help as a lot of the documentaion is in this format and you can search for a term in any installed dev-help documentation by using ```
dev-help -s SEARCHFORTHIS
```

---

### Post by mmxbass on 2008-02-12
> **stroyan said:**
> The gnome window list applet in the gnome panel uses libwnck to list tasks.
Use 'sudo apt-get install libwnck-dev' and browse to
file:///usr/share/doc/libwnck-dev/html/libwnck/index.html
to see documentation of the library.

You can get the actual source for the panel window list applet with this-
apt-get source gnome-panel
You can see the most interesting source in here-
view gnome-panel-2.20.1/applets/wncklet/window-list.c

You can also get the source for the libwnck library-
apt-get source libwnck
The source making xlib calls to get the task information is in here-
view libwnck-2.20.1/libwnck/screen.c
They don't have mono/C# bindings for this thing in DEB do they? I keep seeing some gnome-desktop-sharp package that offer them but they all seem to be RPM junk.

---

### Post by aks44 on 2008-02-12
> **hexnet said:**
> They don't have mono/C# bindings for this thing in DEB do they? I keep seeing some gnome-desktop-sharp package that offer them but they all seem to be RPM junk.

You mean, C# junk packaged in RPMs? (you should have seen this one coming... ;))

</tongueInCheek>

---

### Post by mmxbass on 2008-02-12
It doesn't matter now, I found Python bindings for it.

---


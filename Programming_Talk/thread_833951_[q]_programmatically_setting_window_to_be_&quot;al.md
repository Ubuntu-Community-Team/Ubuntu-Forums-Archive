---
title: "[q] programmatically setting window to be &quot;always-on-top&quot;?"
date: 2008-06-19
forum: Programming Talk
---

### Post by marindev on 2008-06-19
Hi all,
I need a C/C++/X11/Xt/Xm application to start up, be and remain always-on-top (of other applications on screen). From yonder days I recall you could set hints for the Motif-windowmanager, to have a window be always-on-top. 

How to do this on the Ubuntu platform, either by hinting the window-manager (performing the 'On Top' in the window-menu), or by some library-call in code?

Thanks!
Harry


edit: I'm using the default Ubuntu setup: gnome and metacity (which I understand now, is light on features for the matter at hand)

---

### Post by 23meg on 2008-06-19
Moved to Programming Talk.

---

### Post by RIchard James13 on 2008-06-20
In Gnome using GTK you can try
[gtk-window-set-keep-above]("http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-keep-above")

or

[gtk-window-set-transient-for]("http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-transient-for")

Also if the system is using Compiz you can tell Compiz to always keep certain programs on top using ccsm.

Have the window for your program running
Run cssm
Click Window Management
Click Window Rules
In the line called Above click the + sign
now click the grab button and click on the window 
If it doesn't work try changing the top drop down box from window-class to window-title and back to window-class
Click add when the name of the program appears in the value box.

---

### Post by marindev on 2008-06-20
Thanks Richard,
unfortunately the app is implemented using X11/Motif; also, since I don't want to fiddle too much with the standard Ubuntu install, thus keeping metacity as windowmanager, another solution was in order; I found a few klugdes: devilspie seems to be able to do the job (and then some), and the one using now, wmctrl ([http://sweb.cz/tripie/utils/wmctrl/]("http://sweb.cz/tripie/utils/wmctrl/"))
 , a small tool which allows interaction with EWMH/NetWM compatible X Window Managers, amongst which is metacity.

Harry

---


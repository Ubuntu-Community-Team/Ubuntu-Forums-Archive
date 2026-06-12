---
title: "Commandline"
date: 2008-08-06
forum: Programming Talk
---

### Post by kedarm on 2008-08-06
Hey,

Is there any way to give the following attributes/property to a program when opening it from commandline -

a) The size of the window (whether fully maximised/minimised/etc)

b) Whether the window should always stay on top or on the visible workspace?

c) Which workspace it should open on?

---

### Post by LaRoza on 2008-08-06
> **kedarm said:**
> Hey,

Is there any way to give the following attributes/property to a program when opening it from commandline -

a) The size of the window (whether fully maximised/minimised/etc)

b) Whether the window should always stay on top or on the visible workspace?

c) Which workspace it should open on?

That would depend on the window manager.

---

### Post by KingTermite on 2008-08-06
You would probably to do something like:
a) query what window manager is being used
b) use WM APIs to iterate windows and find out which one you program is running in
c) use WM APIs to determine attributes of that window

This is all mostly guesswork, but this is likely how you'd have to do it.

---

### Post by kedarm on 2008-08-07
I use GNOME and I presume its Nautilus doing all the windows managing.

Once the window opens, a right-click and selection from the list is all it takes. But, is there some way to find out what is the exact command that happens (internally?) when we click..

---

### Post by samjh on 2008-08-07
Gnome typically uses Metacity as the window manager.  Nautilus is a graphical file management application.

I don't know how you'll accomplish what you want to accomplish (partly because I don't really know what it is you want to do!), but take a look at the GDK reference library.  GDK is an abstraction layer between Gnome and whatever windowing system is running.
[http://library.gnome.org/devel/gdk/stable/](http://library.gnome.org/devel/gdk/stable/)
The Windows subsection might be of particular interest to you.

---

### Post by mssever on 2008-08-07
> **samjh said:**
> Gnome typically uses Metacity as the window manager.
That's correct, but many Ubuntu users are running Compiz as their window manager--Compiz is the default in many cases.

---

### Post by samjh on 2008-08-07
> **mssever said:**
> That's correct, but many Ubuntu users are running Compiz as their window manager--Compiz is the default in many cases.

True.  But whatever the window manager, GDK should be able to let him access what he needs without getting WM-specific.

---

### Post by Yannick Le Saint kyncani on 2008-08-07
With kde, there are preferences to set up things like that.

Right-click on a window -> configure window behavior -> window-specific settings.

For example, here amarok is always on top, konqueror is always maximized, ...

---

### Post by dtmilano on 2008-08-08
Take a look at devilspie (it's in the repos)

---

### Post by ibuclaw on 2008-08-08
**wmctrl** is another app that you'll be interested in too.

Just remember, while most window managers use "workspaces", the odd few use "viewports" (such as compiz) instead.

Regards
Iain

---

### Post by kedarm on 2008-08-09
I apologise for being so vague with my question.

Here is a more precise form -
I want a command that will open notepad such that -
1) the notepad window has dimensions - height = 100% and width = 20%
2) the notepad window is at the rightmost corner of the screen
3) it is visible on all the workspaces

I use Ubuntu 8.04 and am working with the defaults that come with the install.

I tried reading some manuals, but most of it goes over my head. The intention of this program is to be able to make a script where notepad (or any application) opens in a particular fashion every time I run the script.

Thanks

---

### Post by mssever on 2008-08-09
> **kedarm said:**
> 1) the notepad window has dimensions - height = 100% and width = 20%
Many programs provide a geometry option to set the window size. I don't know of any way to control window placement without requiring the user to have some additional software installed that knows how to talk to their window manager. The sticky attribute is also window manager-specific.

---

### Post by Alasdair on 2008-08-09
Check out the extended window manager hints (EWMH) specification. It allows you to tell the window manager where and how it should display your application. Remember however that the window manager might decide to simply ignore your application's requests.

[http://standards.freedesktop.org/wm-spec/wm-spec-1.4.html](http://standards.freedesktop.org/wm-spec/wm-spec-1.4.html)

---


---
title: "How can I emulate a mouse click event"
date: 2007-12-12
forum: Programming Talk
---

### Post by yinglcs2 on 2007-12-12
Hi,

I have a GTK application.
How can I emulate a mouse click event at a specific location (x,y)in
my code so that my GTK application will response to it as if a user
has clicked at the same location?

The reason i need this is i would to automatically testing of my gtk
application.

Any help is appreciated!

Thank you.

---

### Post by engla on 2007-12-12
Look at the documentation for gtk.gdk.Event [1], maybe you can create a new event object yourself, then you emit a button-press-event signal on the widget that you want to receive the click. (widget.emit("button-press-event", event)) or something like that.

[1] pygtk.org is a documentation site. there is lots of documentation, but a bit hard to get the overview of course.

---

### Post by segalion on 2007-12-12
> **yinglcs2 said:**
> Hi,

I have a GTK application.
How can I emulate a mouse click event at a specific location (x,y)in
my code so that my GTK application will response to it as if a user
has clicked at the same location?

The reason i need this is i would to automatically testing of my gtk
application.

Any help is appreciated!

Thank you.

Do you known [http://ldtp.freedesktop.org/wiki/](http://ldtp.freedesktop.org/wiki/) ?

Its for testing purpose. I.e. for click you have [http://ldtp.freedesktop.org/user-doc/click.html](http://ldtp.freedesktop.org/user-doc/click.html)


A more simple way maybe xmacro (in ubuntu repositories)
echo -e 'MotionNotify [x] [y]\n ButtonPress [n] \n ButtonRelease [n]' | xmacroplay

---


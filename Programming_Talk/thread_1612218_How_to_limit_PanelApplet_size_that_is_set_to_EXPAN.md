---
title: "How to limit PanelApplet size that is set to EXPAND_MAJOR ?"
date: 2010-11-02
forum: Programming Talk
---

### Post by unimatrix on 2010-11-02
I need to use the PANEL_APPLET_EXPAND_MAJOR panel applet flag, so that I always know how much space I have to work with. But now the applet will take all the space it can. How do I prevent this while still use the flag? I know it is possible, because Window List does it.

Let's look at this hypothetical panel arrangement:
**...][applet1][MY_APPLET---------][applet2][...**
So, when I right-click on my applet, I want to get the applet's popup menu. And when I click on the empty area marked as "---------" I want to get the Panel's popup menu.
How do I do this?

---

### Post by unimatrix on 2010-11-03
OK I figured out the only way to do this is by using the following function:
[http://library.gnome.org/devel/panel-applet/stable/panel-applet-panel-applet.html#panel-applet-set-size-hints](http://library.gnome.org/devel/panel-applet/stable/panel-applet-panel-applet.html#panel-applet-set-size-hints)

However I do not understand it due to bad documentation.
Why does it need an array of min-max sizes? I just need one. Also, when I try it my applet gets the width of 1 pixel allocated all the time.

---

### Post by unimatrix on 2010-11-03
Well it turns out the documentation is lying and that there is a bug.

[http://www.kuliniewicz.org/blog/archives/2008/10/13/documentation-always-lies-gnome-panel-applet-edition/](http://www.kuliniewicz.org/blog/archives/2008/10/13/documentation-always-lies-gnome-panel-applet-edition/)

---


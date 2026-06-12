---
title: "PyGTK Applet Transparency"
date: 2008-06-08
forum: Programming Talk
---

### Post by zanelightning on 2008-06-08
I have written a GNOME panel applet using PyGTK, but I would like to the applet's outermost container to be transparent. I've searched around, but I mostly find people trying to create shaped windows, and I feel like I don't need something that involved.

Here's an image of my applet on the left and the weather applet on the right; my panel is transparent, and as you can see, the weather applet makes itself transparent. I'd like to be able to make the outermost gray box transparent.

[IMG]http://img519.imageshack.us/img519/8936/panelro0.png[/IMG]

I'd like to use the simplest method possible; will I have to use Cairo or a pixmap?

Thanks in advance

---

### Post by Quikee on 2008-06-09
Do something like this:

[PHP]def onChangeBackground(self, applet, type, color, pixmap):
    applet.set_style(None)
    rc_style = gtk.RcStyle()
    applet.modify_style(rc_style)
    if (type == gnomeapplet.COLOR_BACKGROUND):
        applet.modify_bg(gtk.STATE_NORMAL, color)
    elif (type == gnomeapplet.PIXMAP_BACKGROUND):
        style = applet.style
        style.bg_pixmap[gtk.STATE_NORMAL] = pixmap
        self.applet.set_style(style)[/PHP]

and connect to applet "change_background" signal:

[PHP]applet.connect("change_background", self.onChangeBackground)[/PHP]

Applet is the applet you get from the factory method.

I hope it helps.

---

### Post by zanelightning on 2008-06-21
Ok, thanks a lot. Fortunately, this makes the applet transparent; however, the space between the little colored score-boxes does not disappear. I tried connecting callbacks for some of the widgets that contain the score-boxes, but I guess this event only exists for applets. How would I do this, what event should I use?

---

### Post by zanelightning on 2008-07-31
Any suggestions?

---

### Post by Quikee on 2008-08-01
> **zanelightning said:**
> Any suggestions?

Sorry.. I have none. 
Can you provide some example code with the problem so I can try to solve it?

---


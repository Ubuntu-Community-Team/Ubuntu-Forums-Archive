---
title: "interpreting xwininfo report"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by foberle on 2012-08-12
I've used CompizConfig Settings Manager a few times to force placement of windows (why doesn't Ubuntu save the last position? Is there a way to make it do this?). I used xwininfo, selected a screen, and then used the "Absolute upper-left X", "Absolute upper-left Y", "Width" and "Height" settings it reported in CompizConfig Settings Manager. Tedious beyond belief for a modern O/S, but it works.

I then searched all over the place for information on the other parameters that xwininfo reports. Many, many sites list these parameters, but I couldn't locate any that explains what they are. I'm delighted to know that my bit gravity and window gravity states are both "NorthWestGravity," but what does that mean? In this example I'm guessing maybe the screen origin point for measurements (in this case, equivalent to Upper Left), but if that's the case, why would it be repeated for every window?

Does anyone know of a source that explains what all the parameters xwininfo represent? Thanks much for any help.

-Frank

---

### Post by JKyleOKC on 2012-08-12
Here's the first hit I got when googling "NorthWestGravity" but it doesn't seem to be extremely clear: [http://tronche.com/gui/x/xlib/window/attributes/gravity.html](http://tronche.com/gui/x/xlib/window/attributes/gravity.html)

I've found that the "geometry" attribute reported by xwininfo is the only one that I really use.

---

### Post by foberle on 2012-08-12
Thanks much, Jim. It didn't occur to me to search for the name of a specific attribute as I was looking for something that covered most of them. The page you directed me to seems to be such a resource, but you're right that it isn't very clear (mostly because it assumes a lot of knowledge that I simply don't have).

I guess I'll just stick to the position numbers and ignore the rest - it was just curiosity anyway.

Frank

---

### Post by JKyleOKC on 2012-08-13
I'm a bit curious also, so I backed up through that URL to [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/) and found that it's the detailed manual for programming the X window system, which is the base on which most Linux GUIs (including that of Xubuntu) rest. It's all rather interesting -- but extremely detailed.

I scanned through the first chapter; I don't pretend to understand it well enough to write a successor to XFCE's window manager by any means, but it put the output of xwininfo into perspective.

I didn't mention, before, taking a look at "man xwininfo" but it describes a number of options that are available for filtering the output report. I'm beginning to get the idea that the "gravity" attributes are significant when moving a child window within its parent, but just what they do is still a bit mysterious...

---


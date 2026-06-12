---
title: "mouse control?"
date: 2011-02-05
forum: Programming Talk
---

### Post by waspinator on 2011-02-05
Hi,

I would like to control the mouse pointer location and clicks. I don't really care which language it uses, although I would prefer python, vala, or mono. I'm looking for something simple like below:

```
getMousePosition()
setMousePosition(x,y)
moveMouse(delta_x, delta_y)
mouseClick(button)
```

I think this should be done through X and not GTK/QT.

Does something like this exist?
Thanks

---

### Post by jimi_hendrix on 2011-02-05
You should probably check out Xlib.  I know that it has python bindings also.

---

### Post by worksofcraft on 2011-02-05
> **waspinator said:**
> Hi,

I would like to control the mouse pointer location and clicks. I don't really care which language it uses, although I would prefer python, vala, or mono. I'm looking for something simple like below:

```
getMousePosition()
setMousePosition(x,y)
moveMouse(delta_x, delta_y)
mouseClick(button)
```

I think this should be done through X and not GTK/QT.

Does something like this exist?
Thanks

At a low level you will have to push mouse events to the X11 event queue using [XSendEvent]("http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html")

There is one big problem with this and that is that X11 incorporates a flag to discriminate XSendEvents from genuine ones and so some applications have been deliberately programmed to reject these events in an attempt to thwart macros.

If that is going to be a problem then you must implement your own mouse driver that will accept virtual mouse movements from other programs and stuff them into the x11 queue as were they genuine user mouse activity. Alternatively you can hack the x11 source code to always clear the "send event" flag ;)

---

### Post by waspinator on 2011-02-07
I have found exactly what I was looking for with PyMouse. This (along with probably 1000s of other similar, feature enhancing projects) should really be included in standard python.

It's really easy to use. The documentation is linked below:

[https://github.com/pepijndevos/PyMouse/wiki/Documentation](https://github.com/pepijndevos/PyMouse/wiki/Documentation)

---


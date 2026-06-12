---
title: "xlib"
date: 2012-11-01
forum: Programming Talk
---

### Post by thedardanius on 2012-11-01
Ok, Im getting a lot of problems.
As some of you know, Im a windows programmer, now also learning linux. So I&#7743; willing to use xlib. But I found out after reading ome of the manual that xlib works a lot differently than the winAPI, and I really need some tutorials on xlib from basic to advanced window maintenance. I dont get the following parts (if any of you know xlib):
- how to get keycode from events KeyPress and KeyRelease (im using a bool key[256] array to store all the keys, at least that worked fine on windows.)
- do I need XSelectInput to get the events or dont I need to specify any flags to use the event?

Ihve got a feeling its gotta be a long way to learn xlib...

---

### Post by satsujinka on 2012-11-01
Here's a tutorial:
[http://tronche.com/gui/x/](http://tronche.com/gui/x/)

If I may ask, why aren't you using a toolkit? GTK+ or QT are much easier to use than Xlib or XCB.

---

### Post by juancarlospaco on 2012-11-01
Make your first App on Qt, when you finish and its stable, then start going lower levels...

---

### Post by thedardanius on 2012-11-02
The same for:
Why didnt you use sdl on windows? winAPI is a lot harder...
I choose the hard way because I want my engine to be independant from 3rd party libraries (expect Im using BASS for sound rendering. Cant implement that myself yet and of course OpenGL, but I assume almost on every system OpenGL is installed).

---


---
title: "[SOLVED] How to make a GUI Application full screen"
date: 2008-11-26
forum: Programming Talk
---

### Post by brijith on 2008-11-26
Hai All,
   I would Like to know, how to make a gui Application full screen. I used to develop application using Python + Pygtk. Also How to embed html in pygtk windows

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by loell on 2008-11-26
for html embeding you could use [gtkmozembed.html]("http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html")

and for fullscreen, gtk c has **gtk_window_fullscreen() **
in pygtk it's [B]  gtk.Window.fullscreen()
[/B]

---

### Post by bruce89 on 2008-11-26
I'd take a look at python-webkitgtk. I don't know how it works, but webkit.WebView is the main class.

---

### Post by brijith on 2008-11-27
> **loell said:**
> for html embeding you could use [gtkmozembed.html]("http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html")

and for fullscreen, gtk c has **gtk_window_fullscreen() **
in pygtk it's [B]  gtk.Window.fullscreen()
[/B]


can any one give more examples on **class-gtkmozembed** ...:)

---


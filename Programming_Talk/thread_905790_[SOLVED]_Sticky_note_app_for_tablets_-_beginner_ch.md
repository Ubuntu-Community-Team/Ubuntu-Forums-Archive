---
title: "[SOLVED] Sticky note app for tablets - beginner challenges GTK+"
date: 2008-08-30
forum: Programming Talk
---

### Post by mkarnicki on 2008-08-30
Hi guys,

I'm a beginner programmer, I have not written a linux app before, not mentioning some scripting (plus web programming). Since I've got a tablet notebook, I challenged myself to **make a handwritten-sticky-note app**, just like the one on Vista (Tomboy notes and other of it's kind are simply another category).

Those of you who have seen it before will surely notice the similarities. I designed it in Glade, so that it looks almost the same as the one mentioned above (would I breach any copyright laws or something doing so?).

To get to the point - I need some hints on GTK+, what element should I use to acquire simple strokes with pen/wacom pen, no candy looking, simple black lines - **GtkImage or GtkDrawingArea **?

I'm studying the Xournal app source (handwritten note taking app, similar to Journal on Widows), but it seems it's too much for what I need. I am aware of lack of my knowledge (I have programmed in C/C++ before, but not for GUI apps), but that's better then writing a tic-a-toe game.

Any hints where to start/read/look for, will be appreciated. I find
[http://developer.gnome.org/doc/GGAD/cha-canvas.html](http://developer.gnome.org/doc/GGAD/cha-canvas.html)
somewhat helpful. Any ideas?

[EDIT] I found what I was looking for: [http://developer.gnome.org/doc/GGAD/z177.html](http://developer.gnome.org/doc/GGAD/z177.html) Nevertheless any ideas are welcome!

---

### Post by kknd on 2008-08-31
For drawing, you can create a cairo context from a GtkDrawingArea and draw in it!
Maybe you can control the "strength" of the stroke by calculating how many time the user spend in a region.

---

### Post by mkarnicki on 2008-09-02
Thank you! I have also found as a reference such apps as VirtualPaper and KanjiPad, and the second one uses intensely Glib (pixmaps, etc), which seems the simplest and most (?) adequate resources for what I need.

I have seen your job on Lua etc - good work!

---

### Post by kknd on 2008-09-02
> **mkarnicki said:**
> Thank you! I have also found as a reference such apps as VirtualPaper and KanjiPad, and the second one uses intensely Glib (pixmaps, etc), which seems the simplest and most (?) adequate resources for what I need.

Nice! Don't forget to open source your application :).

> **mkarnicki said:**
> 
I have seen your job on Lua etc - good work!


Thanks!

---

### Post by mkarnicki on 2008-09-02
> **kknd said:**
> Nice! Don't forget to open source your application :).


Sure thing :D ! I'll let know how's going. For now I'm getting hold of Gtk and Glib knowledge. (Xournal and VirtualPaper are nice applications, also Tomboy with VirtualPaper plugin. Nevertheless a generic handwritten note taking app such as I mentioned before is a good idea for a start. Especially for tablet guys.)

---


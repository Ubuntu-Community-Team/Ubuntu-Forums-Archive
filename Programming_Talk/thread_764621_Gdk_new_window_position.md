---
title: "Gdk new window position"
date: 2008-04-24
forum: Programming Talk
---

### Post by dosh on 2008-04-24
Is there a way to position a new gdk window to a pixel position on the screen. gdk_window_new command seems to randomly position them all over the place even after setting windows x and y attribrutes. I know I can use gdk_window_move afterwards but was wondering if I can do it at the first gdk_window_show command.

---

### Post by descendency on 2008-04-24
edit: Just re-read your post (somehow I missed the last sentence).

I don't understand why you would need to wait to move the Window. Your user will never see the difference.

---

### Post by dosh on 2008-04-24
I am using GDK to create a shaped window and draw onto using cairo to be able to draw onto using (GDK) as someone showed me I need attach it to an event and that event they suggested was GDK_EXPOSE (when the window has been mapped). So the window is showing on the screen and by using gdk_window_move (I'm using C) it would be displayed before the move, not the best visually.

---

### Post by bruce89 on 2008-04-24
I'd assume you can call [FONT="Courier New"]gdk_window_move[/FONT] before [FONT="Courier New"]gdk_window_show[/FONT].

---

### Post by dosh on 2008-04-24
It seems I didn't check a few things, the problem is not when you start the program, but rather if you start the window a number of times while it is still running the first time. I mean having the same program running a number of times.

---


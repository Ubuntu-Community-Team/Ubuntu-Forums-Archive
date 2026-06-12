---
title: "glade-3 tutorial?"
date: 2008-03-24
forum: Programming Talk
---

### Post by Kevin Fischer on 2008-03-24
Does anybody know where I can find a (complete) tutorial on how to use glade-3 and libglade to implement a user interface (in C)?

I want to be able to do it properly, not just using the plugin to generate C code.

I found [this tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html"), but it is quite incomplete and doesn't really help much.

Any ideas? I've been searching for some time...


Note:
There's an old forum question about this, but the answer is wrong (glade-2 and glade-3 are very different when it comes to C because glade-3 no longer generates C code without a plugin).

There is also a glade tutorial on the forums, but it's for glade-2 and python.

---

### Post by Kadrus on 2008-03-24
I found Micah's tutorial to be good..maybe a bit incomplete..anyway..I don't think you will find a lot of tutorials for Glade 3..so I suggest using Glade 2..
Take a look at this..it might help
[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/)
Good luck(^_^)

---

### Post by Kevin Fischer on 2008-03-24
Yeah, I saw a lot of glade 2 tutorials out there; I really think that avoiding generated code is a good thing, though (avoiding having to recompile and all that).

Well, I'll take a look at glade 2, I suppose, and tinker some more with 3.

Thanks!

---

### Post by bruce89 on 2008-03-24
There is no difference between glade files made by glade 2 and glade 3 (not functionally anyway). The UI of glade-3 is a lot better however.

GTK+ 2.10.x and above has something similar to libglade, called GtkBuilder.

---


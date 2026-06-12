---
title: "glademm and kdevelop/anjuta"
date: 2006-11-12
forum: Programming Talk
---

### Post by gareththegeek on 2006-11-12
Hi,

I'm just starting out with making Linux apps using Gtk and KDevelop/Anjuta (haven't decided which to use yet :D) with the help of Glademm and I'm slightly confused about something :confused:

I have worked through the Gtk tutorials for c++ and that's all fine, but when it comes to using Glade; Glade generates it's main_window_glade.hh/.cc file and it doesn't generate any members for the widgets on the window...

So say I make a window with just a button on it.  How do I get at that button from my main_window derived class and, say, change the its text at run time?

I don't want to modify glade's class to add a member for a button because regenerating Glade's code (if I change something for instance) is going to stomp on those members...

Can anyone help or point me in the direction of some good tuts?

thanks,
G!

---

### Post by daniloeu on 2006-11-12
Hi,

I really think that is not a good idea let glade generate code for you...
If you see on Official Glade's website, you will see that...
[http://glade.gnome.org](http://glade.gnome.org) (Glade can also generate C code, though this isn't recommended for large applications)

So, my recommendation is: Always use XML export (see libglade)...
1) Because, if you need to make some layout modification, it will be a very simple work to you, and the program don't need to be recompiled!

2) If you want to make you program in C, you can. If you want to make code on Python, you can too... And if you want to make you program run on Windows, you can do it.

Portability LAW =)

[]'s

Danilo Cesar Lemes de Paula
[http://www.danilocesar.com](http://www.danilocesar.com)

---

### Post by gareththegeek on 2006-11-13
Cool, thanks!

I'll try out the xml mode!

G!

---


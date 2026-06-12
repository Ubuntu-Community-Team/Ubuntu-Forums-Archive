---
title: "GUI frontends"
date: 2006-08-02
forum: Programming Talk
---

### Post by apjone on 2006-08-02
HI, although i have programed in bash,php,html,vb,basic im a bit stuck with how to build a gui in linux. I am using GNOME and dont know c or c++ . I am willing to learn. So anyone got any suggestions where to get started

---

### Post by louis_nichols on 2006-08-02
wel... there are several ways, actually. you can learn c, for example, and program directly in gtk. for KDE/qt there is also a GUI, called kdevelop, that works pretty similar to VB, except code will be in C also (if I remember correctly).

there's also python-gtk, which is pretty cool...

I don't know how to use any of them, actually. just thought to give you some starters... you won't find any basic in the Linux world, to my knowledge...

---

### Post by Grey on 2006-08-02
PyGTK?
[http://www.pygtk.org/](http://www.pygtk.org/)

GTK interfaces through Python.  I don't think that VB, PHP, or BASIC would help you much in Linux.  ;)  But Python should be fairly easy to pick up, if you have a firm grasp of programming concepts.

---

### Post by moma on 2006-08-02
Gambas is not basic.
[http://gambas.sourceforge.net/]("http://gambas.sourceforge.net/")
Well, it requires some QT/KDE packages.

Agree with "Grey"
Go for 
Python: [http://www.python.org/]("http://www.python.org/")
+
wxPython: [http://wxpython.org/]("http://wxpython.org/")
for portable applications !

---

### Post by louis_nichols on 2006-08-02
ooops...

---

### Post by Note360 on 2006-08-03
you can program in PHP with GUI in Linux, but I can't help you. You may want to look into Mono for VB stuff however I am not sure how far their VB is developed.

---

### Post by VirtuAlex on 2006-08-03
> **apjone said:**
> I am using GNOME and dont know c or c++ . I am willing to learn. So anyone got any suggestions where to get started
You're looking for gui toolkit. Gui frontend is a little bit different animal - it is like when you already have console program, but it takes tons of parameters and you're making nice interface to set them. But you are still making that interface using gui toolkit. Since you're gnome user gtk is natural choice. Would you be KDE user - then qt. Both are cross-platform, so you'll be able to compile your programs for other operating systems too.
> **louis_nichols said:**
> for KDE/qt there is also a GUI, called kdevelop
kdevelop is just ide. You can use it whatever way you like, even to make gtk programs in it, not only qt.

---

### Post by ifokkema on 2006-08-04
> **Note360 said:**
> you can program in PHP with GUI in Linux, but I can't help you.
Yeah, you can play around with GTK apps, created by PHP. I once created a simple game in PHP-GTK to play around with programming GUI's. Main issue is that it's not very portable because of some reason PHP-GTK is not in the repositories. But you can learn about signals and callbacks without having to learn a different language.
More information can be found at gtk.php.net.

If you want to port your stuff over easily, you can then always switch to Python GTK.

---


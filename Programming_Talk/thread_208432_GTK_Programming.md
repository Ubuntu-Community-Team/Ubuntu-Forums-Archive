---
title: "GTK Programming"
date: 2006-07-03
forum: Programming Talk
---

### Post by apoth on 2006-07-03
How do you get into this? I'm coming from the ease of Netbeans Java GUI programming and I've never been able to get into GTK programming, either from C++ or Python - I've found the abstraction of something like Glade just too much over the last couple of years.

Any tips or suggestions? Perhaps there are (very) small open source projects that people would suggest I look at the code for? Maybe something the size of wifi-radar (which I'm about to have a look at). Any IDEs?

---

### Post by Max Luebbe on 2006-07-03
GTK is a C library, I reccommend having a strong knowledge of that before starting.
Helps to know the GLib C library as well, as it is the framework GTK is built on.

For small projects, I work in emacs.
If you're used to something like NetBeans, try out eclipse.
Get familiar with it with your Java experience, as it comes set up for Java work out of the box, and when you're ready install the CDT plugin.

CDT lets eclipse use the gnu tools to do C and C++ programming.
Also having it take care of the makefiles can be a nice bonus.

-My $0.02

---

### Post by apoth on 2006-07-03
GTK, pygtk and... gtkmm is the C++ one then isn't it? I'm already familiar with using Eclipse for Java programming (and I prefer vim :P) so I'll give the CDT plugin a go thanks.

It's more a way of easily knocking together GTK-based (pygtk, etc) GUIs _and_ gluing them though that I'm specifically after.

---

### Post by Max Luebbe on 2006-07-03
Sorry for misunderstanding your post!

I'd try out Pygtk then if you know python.
Python is my favorite way to make rapid-prototypes/try out ideas in 10 minutes.
Seems like thats kind of what you are looking for.

---

### Post by Ubuntuud on 2006-07-04
PyGTK indeed. It's easy, very easy.
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by Daverz on 2006-07-04
You don't need to know any C to use pygtk or one of the other better bindings.  The pygtk reference is quite complete, and the tutorial is pretty good.  There is also an extensive FAQ.  See

[http://pygtk.org](http://pygtk.org)

There are also numerous short articles on pygtk linked there.

As for "getting into it", I'd get the pygtk source distribution and just play with some of the examples that come with it (I can't seem to find a deb with the examples).  Also install devhelp and the pygtk docs.  The packages you want are

devhelp
python-gtk2-doc
python-gtk2-tutorial
python-doc (for python itself)

Then try writing a small project and learn as you go along by referring to the tutorial, reference and FAQ, and perhaps consulting the pygtk mailing list or freenet #pygtk IRC channel if you get stuck.

---


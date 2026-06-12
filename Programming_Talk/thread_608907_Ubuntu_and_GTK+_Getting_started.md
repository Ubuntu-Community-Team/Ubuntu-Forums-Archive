---
title: "Ubuntu and GTK+: Getting started"
date: 2007-11-10
forum: Programming Talk
---

### Post by Talsheir on 2007-11-10
Hi,

I was wondering what the most efficient way would be to get started with developing programs with the GTK+2.x toolkit and my brand new UBUNTU?

Thanks for your feedback

T.

---

### Post by kknd on 2007-11-10
Gtk have a lot of bindings, so you must decide which language you will use.

But, even the Gtk OO wrappers preserve the same base, so learning from the official tutorials should be good.

[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by LaRoza on 2007-11-10
You can use it with Python, a language that is very easy to use. My wiki has references for pyGTK and Python in case you want to try that.

---

### Post by bruce89 on 2007-11-10
The normal GTK+ language is C with GObject, but there are bindings for a huge number of languages, including C++, Java, Perl and Python.

[http://www.gtk.org/bindings.html](http://www.gtk.org/bindings.html)

---

### Post by nrs on 2007-11-10
I find using GTK+ with straight C aesthetically obnoxious. It's still doable, and practical though.

I'm partial to the C++ bindings myself. The documentation is excellent; very good API reference, and decent examples / tutorials, if you do find something that is not sufficiently documented, you can often look at the vanilla C docs.  the mailing list is helpful, it is very intuitive. 

[http://www.gtkmm.org/documentation.shtml](http://www.gtkmm.org/documentation.shtml)

---

### Post by Talsheir on 2007-11-11
Thank you to everyone for your feedback. I was actually looking at doing things in C, even though this might be a bit "old-fashioned".

Anyways, I tried to find GTK+ within the packages that come with Ubuntu 7.04 but couldn't find it. 

I am sure even I could (maybe should) get it from gtk.org directly but was wondering if there was an easier way, i.e. through the Ubuntu packages or maybe Debian?!

Any help regarding the "getting" of the required packages for development is very much appreciated!

T.

---

### Post by geirha on 2007-11-11
```
aptitude search libgtk2
``` you want the package ending with **-dev** (I'm on edgy atm, and the package name might be a bit different on your ubuntu)
and of course, you want the **build-essential** package which installs gcc and make among others

---


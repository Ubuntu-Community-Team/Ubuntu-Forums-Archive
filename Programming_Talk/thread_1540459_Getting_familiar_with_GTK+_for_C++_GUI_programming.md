---
title: "Getting familiar with GTK+ for C++ GUI programming"
date: 2010-07-27
forum: Programming Talk
---

### Post by ChrisBuchholz on 2010-07-27
Hi,

I'm interested it playing with GTK+ framework to learn some C++ GUI programming, and I wanna get a good start on it. So other than the offical documentation <http://www.gtk.org/documentation.html>, which resources should I be aware of?
And are there any tips I should know of before I start?

Have a nice night,
Chris Buchholz

---

### Post by pithdillinja on 2010-07-27
I have found [this page]("http://zetcode.com/tutorials/gtktutorial/") to be very helpful. It's C, not C++, but you may want to try starting GTK+ with C anyways. The guides themselves don't really explain in detail what everything means, so you'll have to do some copying, pasting, manipulating, and seeing the result to find out some things.

I also like the application devhelp: ```
sudo apt-get install devhelp
```

---

### Post by ChrisBuchholz on 2010-07-27
> **pithdillinja said:**
> I have found [this page]("http://zetcode.com/tutorials/gtktutorial/") to be very helpful. It's C, not C++, but you may want to try starting GTK+ with C anyways. The guides themselves don't really explain in detail what everything means, so you'll have to do some copying, pasting, manipulating, and seeing the result to find out some things.

I also like the application devhelp: ```
sudo apt-get install devhelp
```

Thanks you for your quick answer!
I'm pretty determined that I wanna do it in C++, since C++ GUI programming is the target of this journey. That is, as long as there is no really, really good reason to why that is a bad idea.

---

### Post by pbrane on 2010-07-27
C++ bindings for Gtk: [http://library.gnome.org/devel/gtkmm-tutorial/stable/]("http://library.gnome.org/devel/gtkmm-tutorial/stable/")

There is also the Glade Interface Designer if you haven't already seen it. It's in the repos, glade3.

---

### Post by ChrisBuchholz on 2010-07-27
> **pbrane said:**
> C++ bindings for Gtk: [http://library.gnome.org/devel/gtkmm-tutorial/stable/]("http://library.gnome.org/devel/gtkmm-tutorial/stable/").

Oh, thats awesome! Thank you very much.

---

### Post by SledgeHammer_999 on 2010-07-28
Also visit [www.gtkmm.org](www.gtkmm.org) which has the full C++ API reference documentation.

---

### Post by WitchCraft on 2010-07-28
Also visit [www.wxwidgets.org](www.wxwidgets.org) for a better toolkit than GTK.
Well, in some areas.

---

### Post by StephenF on 2010-07-28
Take a look at [Vala]("http://live.gnome.org/Vala") as well.

---


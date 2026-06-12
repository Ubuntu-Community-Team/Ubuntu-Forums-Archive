---
title: "pygtk"
date: 2011-06-07
forum: Programming Talk
---

### Post by Astrognomical on 2011-06-07
Did it die or something? I can't find any +2006 tutorials.

---

### Post by Rubi1200 on 2011-06-07
Hi,
not really an area I am familiar with, but did you look here?
[http://www.pygtk.org/articles.html](http://www.pygtk.org/articles.html)

---

### Post by simeon87 on 2011-06-07
It is dying yes. The reason is that GTK 3 will use introspection to generate the Python bindings, there won't be a PyGTK anymore. See [the latest news item](http://www.pygtk.org/) at PyGTK's website and [PyGObject](http://live.gnome.org/PyGObject) (which is what new applications should start using). So instead of developing GTK and bindings for every language, they can focus on developing GTK and the bindings will be generated automatically.

---

### Post by Pilen on 2011-06-07
I have started out programming in python(my first language) since a couple of months ago.
I love the new gnome desktop, and ubuntu of course. So now I wanted to try programming a few simple applications with a toolkit that fits nicely with gnome3.

The problem is this: Tkinter doesn't sound like a good option because it looks pretty ugly, and seems not to have the capacity to use gnome to the fullest.
I searched around and found PyGTK. Nice! Except this:
"PyGTK-2.24 will be the final major release of PyGTK." - and point future development to PyGObject.

So, my question is: As a beginner who want to start making small apps for the gnome desktop, for learning purposes, where do I start? Am I reaching too high at the moment? Should I try another GUI toolkit to begin with?

The world of python offers a lot, sometimes too much for the beginner. It's hard to know where to start.

---

### Post by simeon87 on 2011-06-07
> **Pilen said:**
> I have started out programming in python(my first language) since a couple of months ago.
I love the new gnome desktop, and ubuntu of course. So now I wanted to try programming a few simple applications with a toolkit that fits nicely with gnome3.

The problem is this: Tkinter doesn't sound like a good option because it looks pretty ugly, and seems not to have the capacity to use gnome to the fullest.
I searched around and found PyGTK. Nice! Except this:
"PyGTK-2.24 will be the final major release of PyGTK." - and point future development to PyGObject.

So, my question is: As a beginner who want to start making small apps for the gnome desktop, for learning purposes, where do I start? Am I reaching too high at the moment? Should I try another GUI toolkit to begin with?

The world of python offers a lot, sometimes too much for the beginner. It's hard to know where to start.

Using PyGObject is the same as using PyGTK now. The differences are minor, it will just take some time before technology catches on. I'm still developing with GTK because it looks native on Ubuntu and yes, you can still use Python for that.

---


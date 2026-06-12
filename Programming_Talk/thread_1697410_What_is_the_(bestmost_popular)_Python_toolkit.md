---
title: "What is the (best/most popular) Python toolkit"
date: 2011-02-28
forum: Programming Talk
---

### Post by ki4jgt on 2011-02-28
The title says it all.

---

### Post by cgroza on 2011-02-28
Toolkit to do what?

For GUI, I think it is wxPython.

---

### Post by ki4jgt on 2011-02-28
Yeah sorry LOL GUI toolkit.

---

### Post by juancarlospaco on 2011-02-28
Sometimes the most popular is not the best...

---

### Post by llanitedave on 2011-02-28
I played around with Tkinter, PyQt4, and wxPython before settling on wxPython.  All of them have their good and bad points.

Tkinter works with Python 3 right out of the box, it's included with the language, and overall its appearance is much improved compared to what it used to be.  It's documentation is pretty nice, but not completely updated.  What killed it for me, though, are the file dialog boxes.  They look horrible.  Every time I go to open or save my work from a Tkinter application, it's almost painful.

PyQt4 looks nice and it seems to have an elegant design.  It takes a little more work to set it up for Python 3, and that part isn't so well documented.

wxPython appears to be a community effort from the ground up, and I respect that a lot.  It's very powerful, although there are a few things I haven't yet figured out how to make it do.  In appearance, my first impression is that it's just as nice as PyQt4.  It seems a little more complex to work with, but that impression is subjective on my part and may not be accurate.  The worst part is that it's not Python 3 compatible yet.

What I really like about wxPython, though, is the amount of documentation available for it.  The book by Robin Dunn, [wxPython In Action]("http://wiki.wxpython.org/wxPythonInAction"), and the tutorials on the [wxPython Wiki]("http://wiki.wxpython.org/FrontPage") are amazingly complete and thorough, and are making it fun to learn.

So, I can't tell you what the best GUI toolkit is, but for my money, wxPython is the one with the best teaching community behind it.

---

### Post by jeffathehutt on 2011-02-28
If you want a more native look in Ubuntu (or any gnome/gtk based distro), you should probably use either PyGTK or wxPython.  PyGTK is easy enough to figure out.  I hear wxPython is good but I have no first-hand experience with it. :)

---

### Post by dodle on 2011-02-28
I personally prefer wxPython. I have tried PyQt and it seemed just as simple as wxPython. If you are mainly programming for a GTK environment, pyGtk probably gives you the most control.

*2 cents deposited*

---

### Post by unknownPoster on 2011-03-01
The question is impossible to answer.

---

### Post by nvteighen on 2011-03-01
Nowadays, the decision is more about look and feel and the DE you're targeting to.

---

### Post by juancarlospaco on 2011-03-01
Urwid

---

### Post by ki4jgt on 2011-03-01
I've tried PyGTK. I can't get it to work. I can, but don't understand it completely. The website being down doesn't help things either.

---

### Post by jeffathehutt on 2011-03-01
It looks like [www.pygtk.org]("http://www.pygtk.org") is up again.  Also, if you are still interested in PyGTK [this tutorial]("http://zetcode.com/tutorials/pygtktutorial/") is excellent.

---

### Post by ki4jgt on 2011-03-01
Thanks for the heads up. Zetcode I've already read. I think it's great.

---

### Post by nvteighen on 2011-03-02
> **ki4jgt said:**
> Thanks for the heads up. Zetcode I've already read. I think it's great.

Install the documentation from the Ubuntu repositories and read it in offline! :) (And I suggest you to install Devhelp, which is a nice documentation browser).

---

### Post by ki4jgt on 2011-03-02
> **nvteighen said:**
> Install the documentation from the Ubuntu repositories and read it in offline! :) (And I suggest you to install Devhelp, which is a nice documentation browser).

Already done :-)

---


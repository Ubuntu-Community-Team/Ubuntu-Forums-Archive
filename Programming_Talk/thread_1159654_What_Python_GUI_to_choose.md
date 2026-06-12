---
title: "What Python GUI to choose?"
date: 2009-05-14
forum: Programming Talk
---

### Post by Xarver on 2009-05-14
Hello, I'm Xarver.
I do programming in python 2.x and want to do a GUI.
I have looked at both wxpython and wxgtk and also pyqt.

I want a nice, well documented, and cross platform library.
To me pyqt has a bad license and Tkinter is ugly.
So, what GUI library shall I use?

I will do development on ubuntu gnome, but
most of my users will use windows as I'm the only Linux guy in my family. I have heard pygtk is hard to distribute on windows with py2exe. What do I do?

---

### Post by krazyd on 2009-05-15
Personally, I would look into [PyQt4]("http://wiki.python.org/moin/PyQt4"). What don't you like about its license? Isn't it GPL with a commercial option?

---

### Post by ajackson on 2009-05-15
From the [PyQt4]("http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#license") page:

> Like Qt v4, PyQt is licensed on all platforms under a commercial license, the GPL v2 and the GPL v3. Your PyQt license must be compatible with your Qt license. If you use the GPL versions then your own code must also use a compatible license.

---

### Post by Reiger on 2009-05-15
Which is to say that you can (a) use PyQt for commercial & closed-source purposes under the commercial license; or (b) use PyQt for GPL'ed stuff under the GPL licenses...

---

### Post by stevescripts on 2009-05-15
> **Xarver said:**
> Hello, I'm Xarver.
... and Tkinter is ugly.
So, what GUI library shall I use?

I will do development on ubuntu gnome, but
most of my users will use windows as I'm the only Linux guy in my family. I have heard pygtk is hard to distribute on windows with py2exe. What do I do?


Xarver,

The stock appearance of Tk (Tkinter, RubyTK...) can be significantly changed by appropriate use of the options database.

Please, take a few minutes (not just you, but anybody who has input on "Tk is ugly"...), and give me specifics about what you find "ugly" with Tk - I assure you that I will pass along complaints to the folks who are actively working on the tcl/tk core ...

As for developing on ubuntu, and distributing on windows, *if* you might be open to a non-Python alternative, I invite you to visit my website [http://www.stevescripts.com](http://www.stevescripts.com) , and click on the Starpack link on the left.  I, and many other folks in the Tcl/Tk world, use starpacks routinely, to develop on one platform, and deliver single-file executables to others for other platforms (including customers..).

I am not familiar with problems with delivering executable python files to windows folks, as my use of Python (to date) is mostly for learning/personal interest, and I have Python installed on my  windows boxes (it *is* a shame, that things like Python, Tcl, et al do not come included on windows ...)


Folks, dont take this as a flame on Python, I kinda enjoy learning/working with it, but the single-file executable delivery, works for me (and others), and is a great time-saver.

Steve

---

### Post by jimi_hendrix on 2009-05-15
i use pygtk

since i use gnome it is natural

---

### Post by Xarver on 2009-05-15
To all the pyqt4 fans, here's why:
I don't want to spend 529 dollars to make a commercial product,
that is why I hate the license.

And this is why tk is ugly:
The buttons and widgets look non-native and very old.

---

### Post by fifth on 2009-05-16
> **Xarver said:**
> To all the pyqt4 fans, here's why:
I don't want to spend 529 dollars to make a commercial product,
that is why I hate the license.

And this is why tk is ugly:
The buttons and widgets look non-native and very old.

I use PyQt only for Open Source projects.

But, if your producing a commercial product which you will profit from, why shouldn't you pay for the tools to produce that product? If you profit from your product its only fair the PyQt makers profit from their product.

---

### Post by galileon on 2009-05-16
Or you could use wxpython. The documentation is a bit sparse and disconnected, but the book WxPython in Action helps a lot, despite being a bit verbose.

---

### Post by Xarver on 2009-05-16
fifth: I don't have money, I don't want to spend a ton of cash just to release something commercial that I made.

Thanks for the suggestions so far.
Can anyone compare the two, pygtk and wxpython, and explain which is better?

---

### Post by galileon on 2009-05-16
> **Xarver said:**
> Can anyone compare the two, pygtk and wxpython, and explain which is better?
Sure:

[http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=zPk&q=pygtk+vs+wxpython&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=zPk&q=pygtk+vs+wxpython&btnG=Search&meta=)

---


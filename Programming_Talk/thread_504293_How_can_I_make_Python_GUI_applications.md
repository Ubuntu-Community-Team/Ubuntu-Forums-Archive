---
title: "How can I make Python GUI applications?"
date: 2007-07-19
forum: Programming Talk
---

### Post by cmat on 2007-07-19
I'm pretty excited about recently picking up on python as my new favorite programming language. However I don't know where to start regarding making GUI applications. I never made one since using VB6 on Windows 2 years ago. I would like my applications to be truly cross platform. Any suggestions on how to get started? I looked some stuff up and I need somebody to point me in the right direction.

---

### Post by Peter76 on 2007-07-19
You need to find a widget toolkit with a Python interface to it. The ones I know of are GTK and wx, of which probably the last is the most cross platform at the moment: [www.wxpython.org](www.wxpython.org) .

Good luck

---

### Post by cmat on 2007-07-19
I made my first form, really cool and easy stuff. Finally I'm writing programs on Linux.  :)

---

### Post by Modred on 2007-07-19
In addition to the preceding two, you could also check out [Tkinter](http://www.pythonware.com/library/tkinter/introduction/) and [PyQt](http://www.riverbankcomputing.co.uk/pyqt/).  Tkinter comes with Python in most cases, but some people find it's widgets less than appealing.

---

### Post by LaRoza on 2007-07-19
If you want tutorials, or free books on Tkinter, I have some resources in my wiki, it is in my sig, "Learn to Program" and it is in the "Library". Tkinter is easy to use, but as said before, it isn't the most appealing, but it is good for basic GUI apps.

---

### Post by Golyadkin on 2007-07-19
I myself just started designing GUIs with Glade and Gazpacho and then simply use pyglade to make them interactive, very simple and very easy.

---

### Post by 3rdalbum on 2007-07-19
For writing GUI frontends in a few minutes, I've got to recommend Pythoncard. It's a bit buggy and not feature-packed, but it's very easy to use, and it's cross-platform (as it uses wx).

---

### Post by tc101 on 2007-07-19
People have mentioned WX and Glade.  In the SPE IDE, there is something called wxGlade.  Is that some combination of the two?

---

### Post by thomasaaron on 2007-07-19
I prefer Tkinter.
There is a Tkinter module built into Python, making it very easy to make cross-platform GUIs.
There are also a ton of great tutorials on it. Just google it.

---

### Post by smartbei on 2007-07-19
Glade is (from it's website) "a User Interface Designer for GTK+ and GNOME". wxGlade copied its functionality for the wx widget set, instead of the GTK+ widget set.

---


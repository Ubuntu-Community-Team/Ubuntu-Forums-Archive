---
title: "Getting started building a GUI in Python"
date: 2012-05-18
forum: Programming Talk
---

### Post by MiXor on 2012-05-18
Hello everyone,

I googled 'Python GUI' and synonyms, and got far too much information :P I don't know where to start from! 
I am getting reasonably familiar with the syntax, and it is indeed good fun, but now I want to start using my Lego! :D 

Just editing this post to mention that I've build a GUI for data acquisition, but with the very visual, very handy and not so open source "LabWindows" made by National Instruments. I'm wondering whether a similar thing exists for Python. 

Many thanks for your pointers! ([http://xkcd.com/138/](http://xkcd.com/138/) , for those who don't know it... )
Aline

---

### Post by llanitedave on 2012-05-19
Are you asking for a toolkit recommendation?  A book?

If you want to build something quick and functional, Tkinter is included with Python, it's relatively simple, and works fine.

If you want full-featured toolkits with native-looking widgets, the two most common recommendations are wxPython and PyQT4.  As for documentation, I haven't seen anything better than the documentation on [http://wxpython.org/]("http://wxpython.org/")

---

### Post by Bachstelze on 2012-05-19
> **llanitedave said:**
> As for documentation, I haven't seen anything better than the documentation on [http://wxpython.org/]("http://wxpython.org/")

I'm not familiar with wxPython, but PyQt's documentation is very good too. There is also a [pretty good book](http://www.amazon.com/dp/0132354187) about it.

---

### Post by PeterP24 on 2012-05-19
I wouldn't recommend Tkinter. It was the first GUI toolkit interface I ever learned - and not that it is hard to learn but it is ugly and missing functionality. Sure you can add tabs functionality and so on by using Tix and other stuff - but I'd rather go with wxPython at this stage. For instance, I don't know how to add printer functionality in Tkinter - at the time I went with Tkinter there wasn't implemented (I believe it isn't implemented yet - unless it lies into some obscure library that extends Tkinter in some way). If you don't believe, take a look at IDLE - it is written in Tkinter - compare how IDLE's menus are layed out, or how simple widgets like the Find window looks. Then go to any gtk or quanta app - and compare.
wxPython is much nicer and it has all the documentation in one place.

I don't know about "LabWindows" - but if it is like a RAD tool in which you drag and drop widgets over some empty window, then you might want to try glade: it appears to work with python too - I googled "glade python" and found a tutorial that teaches you how to do a simple app using glade and python.

---

### Post by snowz on 2012-05-20
I would recommend **PyQt** also. I was trying **Glade** while working with Quickly. It's not bad, but **I like PyQt more**.

---

### Post by llanitedave on 2012-05-20
> **Bachstelze said:**
> I'm not familiar with wxPython, but PyQt's documentation is very good too. There is also a [pretty good book](http://www.amazon.com/dp/0132354187) about it.

It's been a while since I looked, but when I was first trying to decide between them myself, PyQT's documentation was a little more confusing for me.  If I were trying to decide now, I might just flip a coin.

The fact that PyQt handles Python 3 is a plus, although wxPython claims to be working on it.

---

### Post by sam81 on 2012-05-20
+1 for PyQt4, I was working with wxWidgets before and I find PyQt4 much easier to use (e.g. for layouts), and more consistent across platforms (with wxWidgets sometimes there were small differences between the Linux and Windows version of a program)

---


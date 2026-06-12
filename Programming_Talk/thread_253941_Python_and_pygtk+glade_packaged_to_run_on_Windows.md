---
title: "Python and pygtk+glade packaged to run on Windows"
date: 2006-09-09
forum: Programming Talk
---

### Post by [h2o] on 2006-09-09
Hi!

I am developing a program using pygtk and glade. I am developing on my Ubuntu machine, but the program is supposed to run in a Windows environment. How would I package all this in the best way? I know I could install python, pygtk and gtk on all machines on the office where the program is supposed to run, but it would be much sweeter if I could just pack it to a single (or few) executables and just distribute these files to the users computers.
I know of py2exe, but I am a bit concerned if it will function properly with pygtk. Any ideas or personal experiences of this?

(btw, there might be some other library dependencies as well, but I assume that whatever makes pygtk run I can use to make them work as well)

---

### Post by Anything Generic on 2008-05-16
Did you ever find a solution to your question?  I've been wondering this as well.

---

### Post by [h2o] on 2008-05-16
Yes I found a tutorial which explained how to do it. Unfortunately I have forgotten the address.
But it consisted of configuring py2exe (writing a setup.py file for your project) and copying some of the gtk libraries.

---


---
title: "Python Gui"
date: 2006-10-07
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-07
Just downloaded Python 2.4 IDLE.

Can you only make text mode programs with it, or does it have graphics and window-like capabilities?

I've looked through quite a bit of info, and, as far as I can see, it only had basic graphics capabilties. Is that right?

Best,
T

---

### Post by meng on 2006-10-07
I'm a newcomer to Python myself, and I'm not 100% sure of the answer, but my impression is that IDLE itself has limited GUI capabilities, but there are plenty of other tools to write GUI programs.

---

### Post by user1397 on 2006-10-07
to my understanding, you use gtk/glade to write the gui parts of your python programs.

---

### Post by po0f on 2006-10-07
[PyGTK](http://www.pygtk.org/)
[PyQt](http://www.riverbankcomputing.co.uk/pyqt/)
[wxPython](http://www.wxpython.org/)
[TkInter](http://wiki.python.org/moin/TkInter)

Those are the more well known ones.  There are probably a couple more, lesser known ones.

If you are using GNOME, you should probably use PyGTK or wxPython, as these build upon GTK.  If you're using KDE, use PyQt.  In either case, TkInter is just a basic GUI framework.  I have used it a little.  It's easy to use, but not that useful as far as what PyGTK/wxPython and PyQt have to offer.

---

### Post by 3rdalbum on 2006-10-08
If you are looking for a program to assist you with creating a GUI, try Glade. If you're looking to easily create a fully graphical program, take a look at Pythoncard. It's inspired by Hypercard, which rocked.

---

### Post by Max Luebbe on 2006-10-08
I use glade for making my python guis.

Pretty easy to learn and also easy to implement as there are good tutorials all over the internet.

---

### Post by baldy1324 on 2006-10-08
ok this is so easy...
use wxPython - [www.wxpython.org/](www.wxpython.org/)
it has a really good wiki great guide and you can make a notepad in about 10 minutes with the sample code!
there is even an easy gui editor called wxGlade - which is also great

---

### Post by etank on 2006-10-09
If you want a good IDE for Python that allows you to write code but also has the tools to help create a GUI then try [SPE]("http://www.stani.be/python/spe"). It is built with wxPython and it is in the repos.

---

### Post by EdThaSlayer on 2006-10-09
hmmm...finally i can contribute!!
you should start with Tkinter first! Its easy to learn how to use it and takes very little code to write a window!

> 
from Tkinter import*
root=Tk()
root.mainloop()

and the best thing is that there are video tutorials on the main site on how to learn about python and the Tkinter GUI!!!

---

### Post by thomasaaron on 2006-10-09
Awesome. There is also a great, downladable (.pdf) manual for Tkinter.
I think I'm going to try to get a handle on Tkinter first and then mess with GTK.

Thanks for all the help guys.

---


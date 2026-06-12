---
title: "Python Gui Toolkit Comparison"
date: 2006-08-27
forum: Programming Talk
---

### Post by peabody on 2006-08-27
I'm interested in personal testimony from people who've worked with Python gui toolkits what your recommendation is.  I myself have worked with wxPython and am developing in my spare time a multi-threaded gui app that automates downloads of images from image gallery web sites.  It's extremely rough and messy right now, but I think the functionality is definitely there and I just need to clean the code up at this point.  I need to start writing my plugins for it for more popular sites such as flickr :).

wxPython seems very powerful, but I can't help but feel like I'm coding C++ sometimes and not Python since there are so many functions that need to be called and I find myself rewriting and refactoring my code a lot.  The documentation for it absolutely sucks right now too.

Apparently (especially in the Ubuntu world) PyGTK is all the rage these days.  Has anyone worked with both and done a good pro/con comparison of each.  I'm not really in the mood to try and switch (GUI toolkits being such a time consuming thing to learn) but if PyGTK is just soooooo much better I *might* be interested if I get *really* bored.

I'm also interested if anyone uses other frameworks to make wxPython more managable (wax, Dabo).  I've heard about these things but haven't used them.

---

### Post by Daverz on 2006-08-28
I use pygtk, and I have some comments on pygtk here:

[http://ubuntuforums.org/showthread.php?p=1269785#post1269785](http://ubuntuforums.org/showthread.php?p=1269785#post1269785)

(I did get pyqt working on windows.)

If you already know enough wxpython to get your work done, I don't see a compelling reason to switch.  PyQT has less documentation than wxPython.  And pyGtk, while it has excellent documentation, would lose you a potential platform (Mac OS X), and is a little less "windowsy" on windows.

---

### Post by kperkins on 2006-08-28
I think that PyGTK is (slightly) easier to use, but wxPython is definitely better for cross-platform gui development, ie. has a more native feel.
This coming from a newbie in both, so take it with a grain of salt.

---

### Post by kwalo on 2006-08-29
I've been using Tkinter - a Tcl/Tk binding for python. Very intuitive api. It's much easier than pytgtk, or pyqt. It's a wise choice, if you plan to quickly write an app that uses only standard widgets (Buttons, text boxes, etc). To create more sophisticated widget, you would have to draw it yourself, using canvas widget.

For more sophisticated applications I'd recommend pygtk.

---

### Post by dwblas on 2006-08-29
I like Tkinter.  If you include PMW and Tix, it has every widget that I use regularly.  Part of your decision is how much custom programming would be required with each toolkit.  Before Tkinter, I used PyQt which hasn't been mentioned.

---

### Post by 3rdalbum on 2006-08-30
Tkinter rocks in terms of ease-of-use. The only problem is that it doesn't look native.

Apparantly it's possible to use gtkdialog from within Python... so it's like an easy shortcut to a GTK interface.

---

### Post by forrestcupp on 2006-08-30
> **kperkins said:**
> I think that PyGTK is (slightly) easier to use, but wxPython is definitely better for cross-platform gui development, ie. has a more native feel.
This coming from a newbie in both, so take it with a grain of salt.

If I understand what you're saying, I disagree.  I use PyGTK, and I've tried my programs on Linux and Windows.  In both environments my programs automatically took on the default window look.  I really like using PyGTK.  Although, like someone else mentioned, I didn't know that it's not available for Mac.

---

### Post by Daverz on 2006-08-30
> **forrestcupp said:**
> If I understand what you're saying, I disagree.  I use PyGTK, and I've tried my programs on Linux and Windows.  In both environments my programs automatically took on the default window look.

He's talking about feel, though.  The most obvious "feel" difference is the file dialog, although since we're talking about Python, there are ways to invoke the win32 file dialog.  I think there are other more minor feel differences.

---


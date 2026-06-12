---
title: "Need some help with python and gtk"
date: 2010-05-26
forum: Programming Talk
---

### Post by vicox on 2010-05-26
Hi everyone,

I'm trying to develop a todo list in python that lives solely in an indicator. I'm new to GTK, and I'm having a hard time putting widgets like a text entry box into a menu. Has anyone done this before. Tips or links are appreciated. Or does anyone want to help me?

I wrote a blog post about it that contains a mockup: [http://blog.vicox.net/2010/05/26/about-todo-lists-and-indicators/](http://blog.vicox.net/2010/05/26/about-todo-lists-and-indicators/)

Thanks!

---

### Post by oldfred on 2010-05-26
Look at Glade and its builder. You then keep the code separate from the display.

builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

### Post by vicox on 2010-05-26
The problem is, that I can't put a text entry box into a GTK Menu or a GTK MenuItem. I would need to make a custom widget of some kind, but the GTK documentation is very poor and I don't know where to start.

---

### Post by dv3500ea on 2010-05-26
Try looking at [this wiki page]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Python+version") and [this launchpad project]("https://launchpad.net/indicator-application").
Or you could make a panel applet ([see this thread]("http://ubuntuforums.org/showthread.php?t=496185"))

---

### Post by StephenF on 2010-05-26
The thing about menus is they disappear when the a menu option is clicked which seems at odds with what you are attempting.

Maybe you could consider a pop-up window. They are used in the Go to Line feature of gedit (hotkey: Ctrl+I). For more complex needs a dialog box is considered correct.

---

### Post by vicox on 2010-06-02
i think it's good that the menu disappears and gets out of your way. but i won't know for sure until i try it out.

---


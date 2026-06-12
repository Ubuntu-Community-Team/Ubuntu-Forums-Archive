---
title: "Python GTK Development"
date: 2009-07-17
forum: Programming Talk
---

### Post by AndThenWhat on 2009-07-17
Hi,

I am in the process of learning Python.  I plan on just using GTK (ie import gtk).  I was wondering if you can either tell me how to set the size and [x,y] coordinates for buttons etc, or point me in the direction of a tutorial for python + gtk development (I'm not sure if by importing gtk I am using pygtk).

---

### Post by master_kernel on 2009-07-17
> **AndThenWhat said:**
> Hi,

I am in the process of learning Python.  I plan on just using GTK (ie import gtk).  I was wondering if you can either tell me how to set the size and [x,y] coordinates for buttons etc, or point me in the direction of a tutorial for python + gtk development (I'm not sure if by importing gtk I am using pygtk).

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by Can+~ on 2009-07-17
> **AndThenWhat said:**
> Hi,

I am in the process of learning Python.  I plan on just using GTK (ie import gtk).  I was wondering if you can either tell me how to set the size and [x,y] coordinates for buttons etc, or point me in the direction of a tutorial for python + gtk development (I'm not sure if by importing gtk I am using pygtk).

GTK doesn't have that conception of X, Y that .NET uses; it works more like a set of objects packed into each other with rules. It's like using HTML (in fact, .glade files are stored in XML).

Read the [pygtk tutorial]("http://www.pygtk.org/tutorial.html") and [micahcarrick's tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html").

---

### Post by master_kernel on 2009-07-17
> **Can+~ said:**
> GTK doesn't have that conception of X, Y that .NET uses; it works more like a set of objects packed into each other with rules. It's like using HTML (in fact, .glade files are stored in XML).

Read the [pygtk tutorial]("http://www.pygtk.org/tutorial.html") and [micahcarrick's tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html").

Note that the second tutorial uses Glade and Python, not plain text PyGTK.

---

### Post by AndThenWhat on 2009-07-17
Ok when I'm in Eclipse I have code completion but it only works for .'s ... Anything inside parentheses says "__module_not_in_the_pythonpath".

I know this isn't related to my above question but if I can solve it then I will solve that problem and many future ones haha.

---


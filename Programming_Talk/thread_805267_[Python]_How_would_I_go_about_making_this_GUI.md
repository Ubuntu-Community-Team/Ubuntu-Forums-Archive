---
title: "[Python] How would I go about making this GUI?"
date: 2008-05-23
forum: Programming Talk
---

### Post by xelapond on 2008-05-23
Does anyone know how I would go about making a GUI like this in Python?  This is sort of a different issue, but what is the easiest way to make it pop up on a global keystroke?

Thanks, 

Alex

btw, Your probably better off downloading it from [here]("http://encodable.com/cgi-bin/filechucker.cgi?action=landing&path=/&file=Mockup1.png"), because the UbuntuForums image viewer messes it up.  Also, the Grey parts(everything not white) should be 47.3% alpha, which is also not shown here.

---

### Post by Lau_of_DK on 2008-05-24
> **xelapond said:**
> Does anyone know how I would go about making a GUI like this in Python?  This is sort of a different issue, but what is the easiest way to make it pop up on a global keystroke?


For a GUI that simple, there are many ways you can go about it, and probably less extensive ones than this: You can using Qt4 bindings in Python, giving you access to one of the most powerful crossplatform frameworks that I know. With these bindings you can basically drag/drop controls unto form and design it anyway you want, using qt-designer.

Check out this example: [Simple PyQt3 example]("http://www.cs.usfca.edu/~afedosov/qttut/")

From here, its "just" a matter of customizing forms and controls to your design.

Hope its of some use,
Lau

Ps. This thread is a good oppertunity for you oldschool die-hard python-gurus to show us how many GUI libs you know of for Python.

---

### Post by aquavitae on 2008-05-24
Does it matter what gui libs you use?  I know in PyQt you can customise the widget styles a probably achieve what you want, although I've never done it. Basically, you create a widgets containing two text boxes,with  properties set as required (i.e. multiline, scrolling, etc) and then use QStyleSheets, QStyles or simply reimplement the paint method so get it to look the way you want. I'd suggest you have a look at the documentation for more info.  I'm not sure if it will do alpha though - that might be dependant on the window manager, e.g. compiz. 

I'm not certain about the keystroke, but I think theres a say to edit the global shortcuts.  Then you could add a key which calls your program.  Maybe someone else can guide you on this..?

---

### Post by Lau_of_DK on 2008-05-24
However you decide to approach this, you'll find a simple how-to here:

[http://www.metaslash.com/python10/guiBasics.py]("http://www.metaslash.com/python10/guiBasics.py")

/Lau

---

### Post by pmasiar on 2008-05-24
Simplest Python GUI library is EasyGUI, by far.

---

### Post by xelapond on 2008-05-26
Thank you all for your replies, 

I have no problems doing normal GUI's with PyQt, but this one is "different".  I will definately look into the QStyleSheet, becuase then I can use what I already know.

Thanks everyone!

Alex

---


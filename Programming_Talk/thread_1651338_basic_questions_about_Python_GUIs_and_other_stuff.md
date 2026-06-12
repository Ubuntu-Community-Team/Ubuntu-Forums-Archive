---
title: "basic questions about Python GUIs and other stuff"
date: 2010-12-23
forum: Programming Talk
---

### Post by CPat on 2010-12-23
Hi all,

Full symptoms/description of my problem are down, but here is a quick lowdown :
-I ran a dummy GUI with PyFLTK and it won't close by any means except while shutting down the compiler. What is the problem?

Long story : I started today checking out python programming. My end goal is a DJ software not unlike Ubuntu's Mixxx. To this end, I installed IDLE (python IDE), FLTK (GUI toolkit) and PyFLTK (python wrapper for FLTK). Now, looking at the user manual for PyFLTK, I found the following code for a Hello World! project :

```
from fltk import *
import sys

window = Fl_Window(300,180)
box = Fl_Box(20,40,260,100,"Hello, World!")
box.box(FL_UP_BOX)
box.labelsize(36)
box.labelfont(FL_BOLD+FL_ITALIC)
box.labeltype(FL_SHADOW_LABEL)
window.end()
window.show(sys.argv)
Fl.run()
```Compiled it and ran it. The problem is, the windows that appeared couldn't be closed by any means. How do I fix it?

Other related questions :

-I'm considering working on the Mixxx project. How can you reach Ubuntu  software dev teams? Is there a special site/directory, or is it  scattered all around?
-Are there obvious better ways to make a GUI program? How would you  personally do it ? (End result : a traktor or reason clone, with a lot  of knobs, 2d graphics, floating strings of comments, sound wave plots, etc)

---

### Post by juancarlospaco on 2010-12-23
Why do you compiled a hello world Python GUI ?

---


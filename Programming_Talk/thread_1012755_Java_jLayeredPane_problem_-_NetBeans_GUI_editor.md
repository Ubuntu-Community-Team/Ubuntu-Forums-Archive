---
title: "Java jLayeredPane problem - NetBeans GUI editor"
date: 2008-12-16
forum: Programming Talk
---

### Post by metcalfe on 2008-12-16
hello,

i am developing a GUI with netbeans and am using a jLayeredPane for the visualization of some states.
so, i have a background image on a layer, and several coloured circles on another, above it
and when i want to set a state, i bring the corresponding circle to the front
the effect is like traffic lights:P

The problem:
this worked fine as i expected it, until...
while editing a side panel on the app, all the layered pane disappears
this has happened in a previous version of the interface, but as it was a simple test, i re-did it and it didn't happen again, until now.
i can't really seem to be able to reproduce this, but in a nutshell, while editing unrelated items to the layeredpane, the layered pane ceased to be rendered.
any thoughts?

PS - i attached my netbeans project. it is operational, with the exception of the invisible layered pane

---

### Post by Zugzwang on 2008-12-16
Nobody here will read a 95kb source code file. If you want anyone to look at it, please make a minimal example in which you problem occurs.

Also, why don't you just us a JLabel and set its icon whenever you want to change the image displayed?

---


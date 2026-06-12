---
title: "PyQt4 General Threading Question"
date: 2008-06-01
forum: Programming Talk
---

### Post by solarwind on 2008-06-01
Hey all, I'm trying to make a Python + PyQt4 program where I sort of "launch" the GUI from the program. The GUI has some textboxes and labels and such. However, the main program has to be doing its own thing and UPDATE the GUI. That means that the GUI has to run in a separate thread (I think). However, I don't know how to access the widgets in the GUI if the GUI has its own thread.

For example, the main application has a constant job. It has to update the GUI during that job (when something triggers within the job). My question is, how do I access the textboxes and labels in the (separately threaded?) GUI from the main application's thread.

---


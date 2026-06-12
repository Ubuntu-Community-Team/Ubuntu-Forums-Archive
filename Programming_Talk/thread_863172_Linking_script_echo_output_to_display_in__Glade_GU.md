---
title: "Linking script echo output to display in  Glade GUI"
date: 2008-07-18
forum: Programming Talk
---

### Post by KB1LQC on 2008-07-18
I have a script that is at some point outputting data in the shell.  For example: echo"Drive sd${i} is attached".  How would I show this text in the GUI for one or multiple drives with C?  There is some info on this in python but not in C.

---

### Post by mssever on 2008-07-18
> **KB1LQC said:**
> I have a script that is at some point outputting data in the shell.  For example: echo"Drive sd${i} is attached".  How would I show this text in the GUI for one or multiple drives with C?  There is some info on this in python but not in C.
Try making a function that will create and show a dialog containing what you want to output. Then, you can simply call that function wherever you need it.

---


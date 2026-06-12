---
title: "Software Program..."
date: 2009-02-26
forum: Programming Talk
---

### Post by El1iP3S01D on 2009-02-26
What are the steps to creating a Software Program using Python to be used on Debian xfce amd64 and linux users as well?

---

### Post by bapoumba on 2009-02-26
Moved to PT.

---

### Post by namegame on 2009-02-26
Generally, Python is cross-platform. Majority of anything you program that works on Debian will work on Linux, Mac, or Windows.

---

### Post by ajackson on 2009-02-26
> **El1iP3S01D said:**
> What are the steps to creating a Software Program using Python to be used on Debian xfce amd64 and linux users as well?
Well you've decided upon a language and have set a GUI benchmark (xfce), you need to determine which python GUI libraries work on xfce, I'm guessing you'd be better off sticking to tkinter but some of the more knowledgable pythonites might offer other suggestions.

The next stage (or continuation of this stage) is design, jumping on the keyboard and producing code isn't always the best option, following a design does have advantages.

After the design stage you are into the code/test phase, this is where having a design helps as you can code blocks, test them and then build upon them for other parts of the application.

---

### Post by Ferrat on 2009-02-26
I might just be way of base but  "Debian xfce amd64 and Linux" what exactly do you mean???

Debian = A Linux distribution. 
xfce = A desktop environment for Linux?
amd64 = An architecture.
Linux = An OS which handles the first two and runs on the third?

Python as stated is cross-platform, the interpreter handles the differences between platforms as a layer. 

ex. 
```
   OS
    |
Interpreter
    |
Your code 
```

So as you see the code doesn't really touch the OS (half truth), however there can be differences when it comes to some file handling or some libs being dynamic on one OS and static on another etc.

---


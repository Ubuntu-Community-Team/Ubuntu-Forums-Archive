---
title: "Python: Exiting PyQt Interface"
date: 2011-02-02
forum: Programming Talk
---

### Post by Sailor5 on 2011-02-02
Greetings!

So if you exit via the 'x' button with your PyQt application this only closes the User Interface and not the process. My question is simple how do say upon the 'x' button being pressed exit both the UI and the process?

Thanks bye!

---

### Post by cgroza on 2011-02-02
I do not know Qt, but I get the same behavior in wxPython. What I did is bind the close event to a function, and after closing the frame I run quit() and the process is gone.

---


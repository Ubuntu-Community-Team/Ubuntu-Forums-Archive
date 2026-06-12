---
title: "Program launches in terminal, doesn't from launcher"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by devi on 2012-07-12
I am trying to create a launcher on my desktop for a program. I can run the following command from terminal just fine:

mono ~/yWriter5/bin/yWriter5.exe

However, when I put that command in the "command" field of a launcher, nothing happens. I attempted this with alacarte and with gnome-desktop. I made sure that "run as an exe" was checked in the launcher properties. What am I missing?

---

### Post by puntigamer on 2012-07-12
Have you ticked/unticked the "run in terminal" option? I don't really know mono anyway, maybe there should be an option too to lauch exe-s without terminal.

---

### Post by Cheesemill on 2012-07-12
Try using the full path for the .exe file:
```
 
mono /home/<USERNAME>/yWriter5/bin/yWriter5.exe


```
Obviously replacing <USERNAME> with your actual username.

---

### Post by devi on 2012-07-12
Thank you, Cheesemill, that did it! Marking this as solved, with gratitude!

---


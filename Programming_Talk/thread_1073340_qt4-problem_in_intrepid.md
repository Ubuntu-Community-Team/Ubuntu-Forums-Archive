---
title: "qt4-problem in intrepid"
date: 2009-02-18
forum: Programming Talk
---

### Post by nagarajhegde123 on 2009-02-18
hi all...

i just installed intrepid since i wnated to work on qt4

i have slected all packages from synaptic like libqt-4* and qt4-*

i even tried 

sudo apt-get install libqt4-gui

everything is installed but i m not able to see the designer running

x@x-desktop:~$ ps -A | grep qt

 5928 pts/0    00:00:11 designer-qt4

can someone help me out of this...


thanks in advance

---

### Post by Zugzwang on 2009-02-18
Did you start the designer from the terminal? If not, try that since error messages might otherwise be swallowed.

---

### Post by nagarajhegde on 2009-02-18
hey i tried that too...

it is like when i typed designer-qt4 in the terminal nothing appeared 

and the cursor was just blinking in the next line...

---

### Post by scourge on 2009-02-18
Did you try installing the qt4-designer package?

---


---
title: "[SOLVED] remove single characters from multiple filenames"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-07
i have a bunch of files named ** R (01).bin, R (02).bin,** and so on all the way up to **R (2532).bin**

i need to change all of the file names to **01.bin, 02.bin,** etc.

please help me

---

### Post by dorkdork777 on 2008-09-07
I assume you're running Ubuntu. In Add/Remove, there is a program named GPRename - install it, and start it.

On the left hand side navigate to where the files are, which will appear on the right hand side. On the bottom, select the tab "Replace/remove", and set it to replace "R (" with nothing, and click "preview". If you're happy with that, click "Rename", then replace ")" with nothing, then "Preview", "Rename".

Though there is probably a much more efficient way of doing it via the Terminal, you should end up with what you need this way. :)

---

### Post by tjwoosta on 2008-09-07
thanks, ill try that

---


---
title: "[SOLVED] installed Grass, but it is nowhere to be found!"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-10-24
Hi (again)!

I installed GRASS using the synaptic manager, updated, and then rebooted. GRASS is not showing up in the menu. OK so I may have muffed the install - so I ran apt-get install grass from terminal and was told the latest GRASS was already installed. Fine. Where is it? Did I miss something? Forget to run some command? 

Thanks in advance.... :)

---

### Post by cairnzi on 2008-10-24
open shell and type grass on its own, no sudo Etc. and tou will get a menu :guitar:

---

### Post by eatingganesh on 2008-10-24
you rock!!! so simple...and yet so beyond my windows-brainwashed mind....

---

### Post by sdennie on 2008-10-24
For future reference, when a package doesn't install into the menu, you can figure out what executable files it's installed with:

```

dpkg -L name_of_package | grep bin/

```

---

### Post by cairnzi on 2008-10-24
lol mate,forget all you have learned in windows, i myself was with windows for years(Xp Pro)but then i seen the Tux, glad to be of help, please mark this topic as "solved"

---

### Post by cairnzi on 2008-10-24
@ Vor, didnt no you could do it that way, thanks for the advice,@ louieb as he said :guitar:

---

### Post by cairnzi on 2008-10-24
RE:@ louieb, sorry wrong post :lolflag::lolflag:

---


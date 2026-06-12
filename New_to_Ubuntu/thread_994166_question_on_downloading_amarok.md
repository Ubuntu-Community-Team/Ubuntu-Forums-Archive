---
title: "question on downloading amarok"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-11-26
when i go into download on there site they tell me to... Amarok can be installed by installing the amarok package.
then it gives the code
# apt-get install amarok 
do i just type that in on the terminal?

---

### Post by w4ett on 2008-11-26
The long and short of it is Yes:
```

sudo apt-get install amarok
```

---

### Post by jpoRS on 2008-11-26
Yep.

---

### Post by bobnutfield on 2008-11-26
> **||Z0di4C|| said:**
> when i go into download on there site they tell me to... Amarok can be installed by installing the amarok package.
then it gives the code
# apt-get install amarok 
do i just type that in on the terminal?

Exactly, but use sudo in front of the command:

> sudo apt-get install amarok

This is a KDE (works just fine with Gnome, though), so it will pull in a few KDE libraries.  This will not give you any problems.  Great app, too, by the way.  One of the best in Linux.

---

### Post by ||Z0di4C|| on 2008-12-02
thanks all this helped a ton

---


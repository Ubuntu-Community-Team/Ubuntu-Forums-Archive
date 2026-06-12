---
title: "[JAVA] Arrow Keys in Terminal"
date: 2010-12-05
forum: Programming Talk
---

### Post by AAndrew on 2010-12-05
Well, I've noticed lately that some terminal applications written in Java enable you to use the arrow keys to navigate through menus, and create a GUI-like environment in the terminal. (Alike to the BIOS on some computers.)

My question is, how does one create an terminal based application in Java that functions this way?

Apologies if this is posted in the incorrect section, I'm new to these forums...
-Andrew

---

### Post by DaithiF on 2010-12-05
it isn't just java that can do this.  most programming languages (c, c++, python, perl, ruby, php ...etc) have a module / library / bindings for interacting with **ncurses**, which is a c library for implementing this kind of 'GUI' in a terminal.

The only java library i'm familiar with for this is CHARVA, which itself uses ncurses under the hood.

so whatever your langauge of choice, google it and ncurses and you'll find plenty of material to get you started.

---

### Post by AAndrew on 2010-12-05
> **DaithiF said:**
> it isn't just java that can do this.  most programming languages (c, c++, python, perl, ruby, php ...etc) have a module / library / bindings for interacting with **ncurses**, which is a c library for implementing this kind of 'GUI' in a terminal.

The only java library i'm familiar with for this is CHARVA, which itself uses ncurses under the hood.

so whatever your langauge of choice, google it and ncurses and you'll find plenty of material to get you started.

Thank you very much, that's just what I was looking for. :D

---


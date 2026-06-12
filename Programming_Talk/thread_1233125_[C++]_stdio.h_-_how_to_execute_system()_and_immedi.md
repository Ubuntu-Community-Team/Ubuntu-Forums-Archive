---
title: "[C++] stdio.h - how to execute system() and immediately exit ?"
date: 2009-08-06
forum: Programming Talk
---

### Post by credobyte on 2009-08-06
I can't seem to find a way to execute a system command via *system()* ( *stdio.h* ) and exit application immediately.
I need to use it as a launcher for my Java application ( *JAR* ) but it does not want to exit until I close my Java application ( launched through *system("command")* ).

Any ideas/suggestions ?

---

### Post by geirha on 2009-08-06
You want [exec(3)](http://manpages.ubuntu.com/cgi-bin/search.py?q=exec).

---


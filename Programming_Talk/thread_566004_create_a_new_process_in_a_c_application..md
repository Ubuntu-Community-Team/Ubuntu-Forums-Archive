---
title: "create a new process in a c application."
date: 2007-10-02
forum: Programming Talk
---

### Post by nzadLithium on 2007-10-02
Hey

I want my application i'm writing to be able to launch other programs.

I can do this using system("path to process");

If i use the system command it pauses my program until the program it launched finishes.

I want a way to launch a program so my program still functions and if i close my program off it doesnt do anything to the program my program launched.

How can this be done using c?

---

### Post by slavik on 2007-10-02
fork() and exec() are your friends :)

---

### Post by angustia on 2007-10-03
[http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html](http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html)

---

### Post by ansi on 2007-10-03
> **angustia said:**
> [http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html](http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html)

Of course ready-to-use libraries are useful, but some of them only add extra dependencies to the programs instead using standard opportunities, like fork() + exec*().

**nzadLithium**
This article might be useful for you [[COLOR="Blue"]Introduction to C/Unix Multiprocess Programming - Fork and Exec[/COLOR]]("http://www.osix.net/modules/article/?id=641") :)

---

### Post by nzadLithium on 2007-10-03
thx

---


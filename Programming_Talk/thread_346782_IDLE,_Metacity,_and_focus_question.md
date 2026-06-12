---
title: "IDLE, Metacity, and focus question"
date: 2007-01-26
forum: Programming Talk
---

### Post by tweedledee on 2007-01-26
I'm working on a fairly complex program in python which requires a variety of modules open at once.  I prefer to do my editing in IDLE (I've tried many other IDEs and text editors, please spare me the "just change editors"), but with Gnome/Metacity, the "shell window" receives focus but does not raise when I execute.  Considering that between executes, the shell window is usually buried, this is very frustrating.

So does anyone know of a way to convince IDLE and/or metacity to cause that window to raise when it receives focus?  If not, is there an alternative window manager anyone is using under which IDLE does behave that way?  I'd prefer not to set all programs to steal focus, but if that's what it takes I'll do it for the sessions when I'm primarily coding.

---

### Post by Jussi Kukkonen on 2007-01-26
System --> Preferences --> Windows ?

---

### Post by tweedledee on 2007-01-26
> **Jussi Kukkonen said:**
> System --> Preferences --> Windows ?

That only helps if I set focus to follow mouse - then I can have it raise windows after a delay. I'm not really a fan of focus follows mouse, though.

---

### Post by tweedledee on 2007-01-28
xfwm4 behaves the way I want by default, other than some minor theme and keyboard shortcut tweaks.  So I've just replaced metacity.

---


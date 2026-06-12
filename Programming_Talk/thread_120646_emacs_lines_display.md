---
title: "emacs lines display"
date: 2006-01-23
forum: Programming Talk
---

### Post by Dearhell on 2006-01-23
I use the terminal environment through Ctrl+Alt+F1

I would like to know if it's possible to change the number of lines that emacs displays, because it displays too few.

---

### Post by toojays on 2006-01-23
This is not something you can change in Emacs. You need to tell the console to use a different resolution for the console. For a x86 machine, this involves adding an argument like "vga=791" to your kernel boot command, to change the framebuffer mode.

---


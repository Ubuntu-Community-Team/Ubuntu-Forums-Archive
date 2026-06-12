---
title: "Xemacs question"
date: 2006-05-12
forum: Programming Talk
---

### Post by Hoffmann on 2006-05-12
All the time I open a written code with Xemacs, not only the buffer with the code is opened, but also a second one with the following warning: 

(xim-xlib/warning) Can't get fontset resource for Input Method

What can I do to avoid that warning?
Thanks!

---

### Post by ZAxisMapping on 2006-05-17
[QUOTE=Hoffmann](xim-xlib/warning) Can't get fontset resource for Input Method[/QUOTE]

I have the exact same problem.  It definitely seems to be Ubuntu specific.

---

### Post by pattu on 2006-05-20
[QUOTE=Hoffmann]All the time I open a written code with Xemacs, not only the buffer with the code is opened, but also a second one with the following warning: 

(xim-xlib/warning) Can't get fontset resource for Input Method

What can I do to avoid that warning?
Thanks![/QUOTE]

Yep.  Me too.  It does look like an Ubuntu problem.

---

### Post by spiceisland on 2006-06-07
Have you tried starting xemacs with LANG=C in your environment?

E.g.:

[INDENT]gwh@snowball:~$ LANG=C xemacs &[/INDENT]

---

### Post by Hoffmann on 2006-06-07
[QUOTE=spiceisland]Have you tried starting xemacs with LANG=C in your environment?

E.g.:

[INDENT]gwh@snowball:~$ LANG=C xemacs &[/INDENT][/QUOTE]
It works this way.

---


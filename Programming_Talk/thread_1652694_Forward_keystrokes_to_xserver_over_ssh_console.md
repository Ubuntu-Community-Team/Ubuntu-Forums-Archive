---
title: "Forward keystrokes to xserver over ssh console"
date: 2010-12-25
forum: Programming Talk
---

### Post by Dysport on 2010-12-25
The idea is that I open an ssh session (without X forwarding) in which I can run a script, that catches every keystroke in that terminal and forwards it to the window manager (gnome, xfce or kde). 
Does anyone know whether this has ever been implemented in any language?

---

### Post by Arndt on 2010-12-25
> **Dysport said:**
> The idea is that I open an ssh session (without X forwarding) in which I can run a script, that catches every keystroke in that terminal and forwards it to the xserver (gnome, xfce or kde). 
Does anyone know whether this has ever been implemented in any language?

KDE etc. are not X servers, they are window managers. But I don't quite see what you want to achieve. What should those key strokes do?

---

### Post by Dysport on 2010-12-25
> **Arndt said:**
> KDE etc. are not X servers, they are window managers. 
Thanks, corrected.
> **Arndt said:**
> But I don't quite see what you want to achieve. What should those key strokes do?
Well they should be forwarded as if the remote keyboard was locally attached. So from typing in a text to close programs with Alt+F4 they should be able to do what they usually do :)

---

### Post by Arndt on 2010-12-25
> **Dysport said:**
> Thanks, corrected.

Well they should be forwarded as if the remote keyboard was locally attached. So from typing in a text to close programs with Alt+F4 they should be able to do what they usually do :)

How do you select which window should have the focus?

---

### Post by Dysport on 2010-12-25
> **Arndt said:**
> How do you select which window should have the focus?

Either with an attached mouse or with Alt+Tab (or another combination that's being translated into Alt+Tab on the host, respectively). It's not that important though, the idea is just to blindly forward it and the window manager will put it into the window which is selected at the moment.

---


---
title: "how do i drop to multiple terminals with no gui?"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by beelzebufo on 2013-12-22
the title pretty much covers it, just wondering how to close the gui and keep my 2 terminal sessions running, i want to maximize my cpu for the terminal processes.

thanks
beelzebufo

forgot to mention i am using ubuntu gnome 13.10 on a little crappy laptop (dell d620)

---

### Post by Bucky Ball on 2013-12-22
Why use a GUI at all? When you say GUI do you mean the desktop environment? If so, why not just install the server version? That has no DE. Or install a minimal install and don't include a DE. That easy.

---

### Post by Lars Noodén on 2013-12-22
Or install just a window manager and skip usilng a full desktop environment.  [s]XFCE[/s] FVWM does the job nicely.  oroborus is probably the smallest.

---

### Post by ian-weisser on 2013-12-22
Perhaps you have discovered that when you close the GUI, all child processes are terminated...including terminal window tasks.

You could start the process from an existing non-GUI TTY.
For example, CTRL+ALT+F1

Or you can start the process from a terminal within the GUI using the *nohup* command, which will ignore the terminate signal when you logout of the GUI, and redirect output to a file.
See man nohup. It's very easy to use.

If the process is headless (reads/writes files instead of keyboard/display), then you can start it from dbus or Upstart so it won't be associated with the GUI.
That's a bit more complex, but not difficult. Upstart syntax is quite straightforward.

---

### Post by Bashing-om on 2013-12-22
beelzebufo; Hi !

In addition to all the other most excellent means, here is another:
ctl+alt+f2
```

startx -- :1

```
ctl+alt+f8

As an example, one can have as many active terminals as one needs.

[INDENT][INDENT]just my 2 bits worth
[/INDENT][/INDENT]

---

### Post by beelzebufo on 2013-12-22
thanks to all, i did mean without a desktop environment thanks for the correction on that, but the reason i don't just install server and ssh into it is that this is my only computer right now so i do need gnome from time to time as well.  i will try all the other suggestions and get back to y'all on which works best.  

Thanks again
beelzebufo

---

### Post by sisco311 on 2013-12-22
You can also try screen:
[uhelp]community/Screen[/uhelp]

Processes you run in a screen session aren't stopped  when the session is detached. 

You can start a screen session in your terminal emulator (GUI) detach it (or close the terminal or even log out from the GUI) and re-attach the session in a virtual console (CLI) or vice versa.

---


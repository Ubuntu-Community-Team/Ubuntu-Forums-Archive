---
title: "xterm tricks"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by jalirious on 2013-02-01
Hi, does anyone know how to open a new terminal tab and simultaneously close the previous one?

Ctrl+shift+t opens a new tab in the terminal (in the same dir)

But I want the old tab closed at the same time.

[do not suggest the "clear" command ;]

---

### Post by zombifier25 on 2013-02-01
I think you meant gnome-terminal since you can't open new tabs in xterm.
AFAIK, there's no such way. But this works:
```
gnome-terminal & disown & exit
```

---

### Post by tgalati4 on 2013-02-01
Understand that any process started (and still running) in the terminal to be closed will be terminated.

---


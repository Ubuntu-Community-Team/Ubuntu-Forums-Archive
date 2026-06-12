---
title: "Changing Default Terminal (13.10)"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by cha0sthe0ry on 2014-02-16
I was messing around with different terminals, and installed Guake terminal.  I attempted to make it the default terminal, but never succeeded.  Now when I push Ctrl-Alt-T nothing happens, and I have since uninstalled Guake.  How do I go about switching my default terminal back to the vanilla Gnome Terminal?

---

### Post by zealibib slaughter on 2014-02-17
[http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/)
Ill just link to an article instead of going through how to.  Now with guake you just press f12 and it opens if guake is running.  You can add it to your start up program list so it starts every time your system does.  Thats what I do.

---

### Post by Bucky Ball on 2014-02-17
Settings>Preferred applications>Choose your terminal. It may go under another name in Ubuntu but it will be something like 'Preferred Applications'.

---

### Post by steeldriver on 2014-02-17
I seem to remember using update-alternatives after messing with guake myself

```
update-alternatives --config x-terminal-emulator
```

---


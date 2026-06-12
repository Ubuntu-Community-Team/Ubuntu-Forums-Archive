---
title: "Launching GUI before login"
date: 2010-01-28
forum: Programming Talk
---

### Post by ubt_user_0331 on 2010-01-28
Hi, I would like to start a GUI on the login screen.
My assumption is that since X is already running (hence the graphical login screen), I can launch a GUI window.

My current approach is by writing a daemon that tries to perform XOpenDisplay and draw the GUI. I understand that to connect to the X server, the daemon must be run not as root but a different user. It seems that display managers such as GDM is doing something similar but am having trouble understanding how.

The daemon starts normally if it does not try to XOpenDisplay but will fail to start if trying to open display.
I hope someone can give some tips or maybe even a full tutorial? :)

Thanks in advance

---

### Post by ubt_user_0331 on 2010-02-12
The XOpendisplay call always fail, returning NULL. I specified the script to be S99, so it should run last after Xserver is up right?
Anyone can help?

---


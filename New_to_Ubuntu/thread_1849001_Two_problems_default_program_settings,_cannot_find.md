---
title: "Two problems: default program settings, cannot find file on startup."
date: 2011-09-23
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-09-23
OK, so I have two little problems. 

the first is, every time I start my computer, it says it cannot find /home/(username)/documents/GTA2INSTALLER. I tried to install that a while ago, but then I uninstalled it, and ever since then it pops up like that. the only thing I had in my documents was the unpacked folder of it, not the program. 

And, the other thing: last time I played Mines (minesweeper, included) I was playing around with it, setting it to custom, with 100x100 grid, and 1 bomb, and it froze, and now when I open it, it tries to open with my last settings, and is frozen the second it starts. Is there any way to load it with the default settings, so that I may fix it, or if there is any other way to fix it?

---

### Post by sanderd17 on 2011-09-23
For the first problem, it is maybe added to the startup programs. Try seeing that.

For the second one, you could delete the mines settings. Normally settings are inside hidden directories in your home directory. Press CTRL+H in nautilus to show them. Since Mines is part of the gnome-games, it possibly is in one of the gnome configuration directories or in .local (also a settings directory).

If you don't find it that way, launch the gconf-editor (by pressing ALT+F2 and executing that command) and search for a setting.

---

### Post by mschooler93 on 2011-09-23
Thank you, that did it.

---


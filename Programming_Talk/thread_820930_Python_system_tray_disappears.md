---
title: "Python system tray disappears"
date: 2008-06-06
forum: Programming Talk
---

### Post by Gannin on 2008-06-06
I tried to create a simple little program, both in PyQt and PyGTK, which would display an icon on the system tray than you could use to easily switch back and forth between Compiz and Metacity.

The problem is, and this happens with both PyQt and PyGTK, when I use the icon to switch to Metacity, the icon completely disappears from the system tray.  There's still a space on the system tray for it, but it's an empty space... the icon itself disappears and if you click on that space nothing happens.

Any idea why this would happen?

---

### Post by ::: on 2008-06-07
Would you mind showing us the source code?

---

### Post by Gannin on 2008-06-07
It turns out the main problem was calling os.system("metacity --replace") (and the same for Compiz) as when you call either command, it causes the program to block, so when you do it as part of the main loop it causes the entire program to block causing the system try icon to disappear.

The way to fix it is to shove such calls out into a thread, and because calling one command causes the other command to terminate, when you create a new thread for the new command the other thread naturally stops and can get garbage collected.

The program is all done now and seems to be functioning just fine.  I even managed to make a silly little icon for it.

---


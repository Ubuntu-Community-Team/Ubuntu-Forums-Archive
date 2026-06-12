---
title: "Ubuntu 11.10 GUI Problem"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by Rhumar on 2011-12-16
Today I booted up my Ubuntu partition and for a second after I logged in, there was a monochrome gray screen, and then the desktop loaded.  The problem was and still is that there was no side bar with applications, and the top bar did not display any of the buttons like time, internet connection, user, power, etc.  The only buttons on the top bar that I could see were the File, Edit, Go, etc.  Also, the only keyboard shortcut that worked was Ctrl+Alt+T for the terminal.  I rebooted multiple times in normal and safe mode, and ran couple scans from safe mode with no result.  I also used to terminal to run "sudo apt-get update" just in case it fixed it, which it did not.

---

### Post by collisionystm on 2011-12-16
try

unity --reset

in terminal

---

### Post by collisionystm on 2011-12-16
I dont know what your cup of tea is with user interfaces, but you should try gnome-shell. It wont have that problem.

check out

[http://extensions.gnome.org](http://extensions.gnome.org) and you can make it suitable to your liking

---

### Post by Rhumar on 2011-12-17
I tried that command.  It took a long time to run and gave me a couple errors, but it more or less ran the command with no result or change.  If this helps, it is almost like when you end the explorer.exe process in windows.

---

### Post by wildmanne39 on 2011-12-17
Hi, follow the procedure on this page and you should be able to get it fixed.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thanks

---


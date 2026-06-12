---
title: "Removed libasound2 packet"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by aleksandr2 on 2013-08-03
[COLOR=#0000ff]Hi, guys!

I have this kind of problem. After removing the libasound2 packet by typing "apt-get remove libasound2" on ubuntu 10.04 my OS couldn't be booted. How i can resolve this problem? Thank you for replying.[/COLOR]

---

### Post by ajgreeny on 2013-08-03
It looks as if that command will have removed most of your GUI, or at least, a lot of it.  If you can at least boot to a command line you can login to that and try running ```
sudo apt-get install ubuntu-desktop
``` which should reinstall everything you removed.

If you were using another desktop, as in xubuntu or kubuntu, install the appropriate ***ubuntu-desktop** package instead.  You can do the same from recovery mode where **sudo** is not needed for the install command.

---

### Post by aleksandr2 on 2013-08-03
[COLOR=#0000ff]Thank you! This command works![/COLOR]

---


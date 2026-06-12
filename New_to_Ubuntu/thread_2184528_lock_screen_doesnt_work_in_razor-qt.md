---
title: "lock screen doesnt work in razor-qt"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-10-29
have 13.10 installed. lock screen works fine in xubuntu,lubuntu,enlightenment, gnome, and ubuntu. just cant get it to work in razor when i click the lock screen buttons nothing happens. any idea? tks

---

### Post by rburkartjo on 2013-10-30
did some searching and experimenting. if you run xscreensaver-command -lock in the terminal it will lock the desktop and request your password to unlock

---

### Post by rburkartjo on 2013-10-30
you can use this script. call it whatever and make it execute-allow executing file as program.

#!/bin/bash
xscreensaver-command -lock

---


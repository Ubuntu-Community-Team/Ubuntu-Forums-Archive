---
title: "script for desktopnova"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-23
must of had too much turkey yesterday because i deleted a script to stop the program desktopnova. any ideas? tks

---

### Post by rburkartjo on 2012-11-23
found it here it is replace xxx with your password

#!/bin/bash
echo xxx | sudo -S
tray=$(pidof desktopnova-tray)
daemon=$(pidof desktopnova-daemon)

kill -9 $tray && kill -9 $daemon

---


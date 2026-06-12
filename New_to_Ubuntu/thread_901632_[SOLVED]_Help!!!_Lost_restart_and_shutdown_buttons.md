---
title: "[SOLVED] Help!!! Lost restart and shutdown buttons!!!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-08-26
I was trying to get a screenshot of a GDM and suddenly lost my shutdown and restart buttons from the exit menu.:(:(:(:( what did I messed up this time? All I did was follow a post that apparently worked for other people

> echo "chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png" > /tmp/capture

yet, get several error messages and haven't managed to the the screenshot

---

### Post by ffmpegfailure on 2008-08-26
as a temporary solution you can hold alt + f1 which brings up a panel menu, at the bottom of which there is the log out etc. option. There is a bug surrounding this ( I think) which the last time I looked had not been resolved)

---

### Post by philinux on 2008-08-26
System>admin>login window.

Click the local tab and check the box "Show Actions menu"

---

### Post by arashiko28 on 2008-08-26
Thanks!!! I was getting desperated:)

---


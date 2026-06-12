---
title: "Airmon"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-16
How come I can't get airmon to work?

matthew@blackmagic:~$ sudo airmon start wlan0
sudo: airmon: command not found

---

### Post by cariboo on 2008-08-16
Have a look here:

[http://www.aircrack-ng.org/doku.php?id=airmon-ng](http://www.aircrack-ng.org/doku.php?id=airmon-ng)

For help using airmon-ng.

Jim

---

### Post by nicedude on 2008-08-16
The command should be

matthew@blackmagic:~$ sudo airmon-ng start wlan0

but be aware for this to work your wifi adapter must support monitor mode, if your using Ndiswrapper you are out of luck as neither monitor mode nor injection will work in conjunction with Ndiswrapper.

---


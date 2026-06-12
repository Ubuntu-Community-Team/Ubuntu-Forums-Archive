---
title: "bluetooth"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by hellomoto on 2008-11-04
I am trying to get bluetooth to work on my xubuntu 8.10 PC. I have downloaded all the packages and my Bluetooth dongle is recognized in lsusb but thats as far as I get, their is no bluetooth icon like thee is on ubuntu. 

Please help!

---

### Post by model citizen on 2008-11-06
type (in terminal)

bluetooth-applet 

that should sort you out mate. Then if that's cool just put it in the autostarted apps section and you're good to go from booting up.

---

### Post by gn2 on 2008-11-06
This is perhaps a bit out of date but might help: [http://ubuntuforums.org/showthread.php?t=669171](http://ubuntuforums.org/showthread.php?t=669171)

---

### Post by Nepherte on 2008-11-06
What does
```
hciconfig -a
```
give you?

---


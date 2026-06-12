---
title: "Mother Board Info =x"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Solais on 2008-09-20
Hey guys? how can I know whats the manufacturer of my mother board with out opening my pc? :( to get the stuff for the nlite cd and such :)

---

### Post by phidia on 2008-09-20
the command "lshw" should provide you with some info.

---

### Post by Whiffle on 2008-09-20
and "dmidecode"

---

### Post by Solais on 2008-09-20
Thanks :)

---

### Post by mc4man on 2008-09-20
```
sudo lshw -html > hardware.html
```
This gives you the output in a very nice, readable format
Look in home folder for hardware.html

---


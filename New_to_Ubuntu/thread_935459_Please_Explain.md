---
title: "Please Explain"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by drileysr on 2008-10-01
I have just recently installed my first linux OS (kubuntu 8041).Have used windows xp for a couple of years and when I wanted to update firefox 2 to firefox 3 I would download and hit "run" and it would install. I tried to update kubuntu to firefox 3 and couldn't figure out how to download and install it properly. Can anyone walk me thru it? Thanks from an "absolute beginner".

---

### Post by oldos2er on 2008-10-01
Firefox 3 comes with Ubuntu 8.04, including Kubuntu. To update it, open up a Konsole (terminal) and type in the command "sudo aptitude update && sudo aptitude upgrade". This will update your OS and some programs too, including Firefox.

---

### Post by shifty_powers on 2008-10-01
go to the terminal and enter

```
sudo apt-get remove firefox && sudo apt-get install firefox-3.0
```

---

### Post by jamesrl on 2008-10-01
Most of the time on ubuntu when you want to install a program, you can go to the package manager (in kubuntu that's 'adept package manager' in ubuntu its 'synaptic').  You can then browse packages available for installation, and then add or remove programs, and when you select to install a program the package manger will download and install it (and the required dependencies for that program).  However, firefox on 8.04 should be firefox3.0 by default (you can check by Help->About Mozilla Firefox)

---


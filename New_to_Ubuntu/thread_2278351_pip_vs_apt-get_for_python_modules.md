---
title: "pip vs apt-get for python modules"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by Malik_Rumi on 2015-05-15
It seems that some programs are easier to get, or only get, from one and not the other. Is there a post or instruction or a directory that tells which to use to get which modules? Thanks.

---

### Post by sandyd on 2015-05-15
Generally:
apt-get:
[LIST]
[*]Single version of package
[*]Limited number of modules
[/LIST]
pip:
[LIST]
[*]All modules
[*]Can select which package versions to install
[/LIST]

Generally, I would just use create a seperate virtualenv for each program.

That allows you to have finer control over versions and what modules to install.

---

### Post by Malik_Rumi on 2015-05-16
Excellent! Fast, short, and to the point. Thank you.

---


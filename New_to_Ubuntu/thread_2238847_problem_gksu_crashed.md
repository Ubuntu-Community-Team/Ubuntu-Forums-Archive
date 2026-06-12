---
title: "problem gksu crashed"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by engineer2 on 2014-08-10
Hello everyone 
I have a problem with gksu nautilus it is not working on Ubuntu 14.04LTS I googled the error and it appeared that it is a common bug. but i really need to browse the root files .. so are there any alternatives??  :?::?:

---

### Post by mc4man on 2014-08-10
in a terminal
```
sudo -H nautilus
```

---

### Post by whitesmith on 2014-08-10
running```
gksudo
```by itself gives you a more advanced way of running a GUI app. Does this work for you or is this hosed as well?

[edit] Running```
sudo -H nautilus

``` works, but produces a terminal error on my machine.

---


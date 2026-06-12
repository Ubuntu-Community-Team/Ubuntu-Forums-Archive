---
title: "[SOLVED] Pidgin won't open.."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by projecthikari on 2008-08-12
Simple trouble...

Pidgin will not open. I go into my applications to start it, and it simply will not start.

---

### Post by StOoZ on 2008-08-12
try to run from the terminal , I bet it will complain about permissions,or say:
> "pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error"



 if so , do this:
> cd /usr/lib
sudo rm ./libpurple.so.0
sudo ln -s /usr/local/lib/libpurple.so.


---

### Post by projecthikari on 2008-08-12
I'm still having the same trouble. T_T

jen@the-food-court:~$ cd /usr/lib
jen@the-food-court:/usr/lib$ sudo rm ./libpurple.so.0
[sudo] password for jen: 
rm: cannot remove `./libpurple.so.0': No such file or directory
jen@the-food-court:/usr/lib$ 


Thus is what i get...

---

### Post by appi2012 on 2008-08-12
Try reinstalling pidgin. do this:
```
sudo apt-get purge pidgin
```
```
sudo apt-get install pidgin
```

---

### Post by Sygen on 2009-06-11
possibly it never went to your taskbar.  Check upper right. See if it did load >.< couple be as simple as a visual check

---


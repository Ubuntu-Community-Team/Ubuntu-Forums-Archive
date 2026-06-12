---
title: "installing plugins"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-26
Hi again

When I try to install plug ins I get the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

Then when I open a terminal and try to do this I get the message:

dpkg: requested operation requires superuser privilege

Help!!

---

### Post by gandaran on 2008-04-26
run on the terminal
sudo dpkg --configure -a

---

### Post by SOULRiDER on 2008-04-26
After running
```
sudo dpkg --configure -a
```
make sure you update everything, run
```
sudo aptitude update
```
and
```
sudo aptitude dist-upgrade
```

---

### Post by saskatchewan on 2008-04-26
Now there is a Java license and I can't get rid of it.....

It says OK and just fills the terminal.

What do I do?

---


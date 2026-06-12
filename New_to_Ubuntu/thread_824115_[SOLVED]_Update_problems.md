---
title: "[SOLVED] Update problems"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by esedizzle on 2008-06-09
I run ubuntu and when I run my update manager and specifically install updates it says: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 
and the updates are not installed. Please Help.

---

### Post by cdtech on 2008-06-09
Did you run:
```
dpkg --configure -a
```

---

### Post by JoshuaRL on 2008-06-09
You might need to use root priviledges:
```

sudo dpkg --configure -a

```
And you might try:
```

sudo apt-get install -f

```
That tries to fix packages and dependencies through APT.

---

### Post by drs305 on 2008-06-09
to get to where you want to go, as JoshuaRL said try running (with sudo):

```
sudo dpkg --configure -a
```

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cdtech on 2008-06-09
WOW!

You may need to try sudo:

---


---
title: "NetBeans 6.1"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ShrapnelHunter on 2008-05-21
I just got Ubuntu 8.04, and have installed NetBeans 6.1 with the ruby pack. However, when I go to run it, it displays the splash screen, but then crashes(?). I have the latest Java JDK installed, so it should run. Anyone got any tips or advice? :)

---

### Post by kellemes on 2008-05-21
> **ShrapnelHunter said:**
> I just got Ubuntu 8.04, and have installed NetBeans 6.1 with the ruby pack. However, when I go to run it, it displays the splash screen, but then crashes(?). I have the latest Java JDK installed, so it should run. Anyone got any tips or advice? :)

Run it from a terminal Window and watch the output..

---

### Post by jamesstansell on 2008-05-24
ShrapnelHunter, are you still having this problem?  What is the exact error?  How did you install NetBeans and the JDK?

---

### Post by sayakb on 2008-05-24
Try switching to the metacity display manager before running Netbeans:
At a terminal:
```
metacity --replace &
```And do not close the terminal window.

When you're done:
```
compiz --replace &
```

---


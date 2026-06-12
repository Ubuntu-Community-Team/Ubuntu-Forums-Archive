---
title: "OOOHHH I frogot"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by mbele3000 on 2008-08-30
I installed a program using wine off a disk and well now it is in my trash (the program) and now when I try to empty it says I have no permission. How can I work this out?
 
 Thank You MNY

---

### Post by sisco311 on 2008-08-30
Change the owner of the files from a terminal:
```
sudo chown -R *username *~/.local/share/Trash/
```then empty the trash.

---

### Post by mbele3000 on 2008-08-30
no that did not work sorry

---

### Post by gmxgeek on 2008-08-30
Can you resore it? if so then restore it, open a terminal and cd to the folder in which it resides and run
```

sudo rm -f filename

#or for folders

sudo rm -Rf folder

```
this should kill it dead

---


---
title: "[SOLVED] Cedega removal"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ion072002 on 2008-08-02
hello, i know, there already is a topic in here for this, but iti didn't help me. i installed cedega from a .deb file, and i am now trying to remove it.

sudo apt-get remove cedega   doesn't work.
sudo dpkg -l  gives me some info but i don't know what to make of it.
sudo dpkg -r  will just give me an error saying i don't have cedega installed, even if the darned thing is there.


help me please!!!

---

### Post by Fixman on 2008-08-02
> **ion072002 said:**
> hello, i know, there already is a topic in here for this, but iti didn't help me. i installed cedega from a .deb file, and i am now trying to remove it.

sudo apt-get remove cedega   doesn't work.
sudo dpkg -l  gives me some info but i don't know what to make of it.
sudo dpkg -r  will just give me an error saying i don't have cedega installed, even if the darned thing is there.


help me please!!!

```
 sudo apt-get remove cedega-small 
```

---

### Post by ion072002 on 2008-08-02
10x, problem solved

---

### Post by Oldsoldier2003 on 2008-08-02
> **ion072002 said:**
> 10x, problem solved

Please use the thread tools link at the top of the thread and "Mark this thread as solved", it helps others when they are searching the forums, knowing a thread is solved makes for less reading and possibly a quicker resolution when you have a similar issue.

---


---
title: "got an error with a program"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-30
tryed to download limewire but ubuntu is saying that i have a synaptic package manager open but i dont. then i tryed to open the synaptic package manager and i get this error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

i try to enter the command in the terminal but it wont take can someone help me with this.

---

### Post by iaculallad on 2008-07-30
> **edwin2105z said:**
> tryed to download limewire but ubuntu is saying that i have a synaptic package manager open but i dont. then i tryed to open the synaptic package manager and i get this error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

i try to enter the command in the terminal but it wont take can someone help me with this.

As the message imply, drop on your terminal and issue the command

```
sudo dpkg --configure -a
```

---


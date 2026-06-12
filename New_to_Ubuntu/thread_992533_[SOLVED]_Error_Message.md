---
title: "[SOLVED] Error Message"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Connor_Mac on 2008-11-24
Okay so this is my very first post here and I dont know if im in the right spot or not but i cant add or remove any applications, every time ig get the message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone help me?

---

### Post by taurus on 2008-11-24
If you have synaptic, update manager, or add/remove window open, close it.  Then, open a terminal and type

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by jemate18 on 2008-11-24
I guess this thread is solved.. PLease mark it as SOLVED

---

### Post by Connor_Mac on 2008-11-24
> **taurus said:**
> If you have synaptic, update manager, or add/remove window open, close it.  Then, open a terminal and type

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

Thanks a lot man, i really appreciate it. and sorry if this was not what i was supposed to do or if its the wrong section

---

### Post by jemate18 on 2008-11-24
No problem..... This is Ubuntu (Humanity to others) we're always here to help.... 

Happy Ubuntu!

---


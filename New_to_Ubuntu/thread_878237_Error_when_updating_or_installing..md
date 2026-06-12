---
title: "Error when updating or installing."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by YvonneQ on 2008-08-02
I am new to Ubuntu.  After installing the new system I receive an error message (below) when attempting to update or installing new programs:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Does anyone know how to fix this?

---

### Post by mevets on 2008-08-02
Try entering this into the terminal
```

dpkg --configure -a

```

---

### Post by drs305 on 2008-08-02
```
sudo dpkg --configure -a
```
be sure to add the 'sudo' Type your password but you won't see it as you enter it. That's ok - once it's typed, hit ENTER.

---


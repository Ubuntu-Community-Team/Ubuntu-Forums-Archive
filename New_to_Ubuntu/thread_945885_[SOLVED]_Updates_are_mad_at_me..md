---
title: "[SOLVED] Updates are mad at me."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by projecthikari on 2008-10-12
The picture attached speaks 1000 words.

What do I do about this?

---

### Post by jemate18 on 2008-10-12
> **projecthikari said:**
> The picture attached speaks 1000 words.

What do I do about this?

you should have root privileges in order to execute dpkg

type```
sudo dpkg --configure -a
```

---

### Post by OutOfReach on 2008-10-12
Right, jemate18 has got it, you need to run the program as root.

The problem that you had was most likely caused by an interruption (power outage, force quite) during and installation or upgrade.

---

### Post by projecthikari on 2008-10-12
It told me i had something broken (package?), and to use the "Broken 'something' finder" to fix it.

---

### Post by jemate18 on 2008-10-12
> **projecthikari said:**
> It told me i had something broken (package?), and to use the "Broken 'something' finder" to fix it.

Yes... because in some point, your update was interrupted or something...


Applications -> Accessories -> Terminal

Type
```
sudo dpkg --configure -a
```

I hope this solves it.....

---


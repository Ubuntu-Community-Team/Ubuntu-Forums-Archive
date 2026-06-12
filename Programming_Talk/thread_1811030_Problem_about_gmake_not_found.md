---
title: "Problem about gmake not found"
date: 2011-07-24
forum: Programming Talk
---

### Post by kelvin490 on 2011-07-24
I have a set of C program but when I use "make all" to compile, it goes:
 
/bin/sh: gmake: not found
 
Is it a path problem? Or do I need to install something?
 
Thanks for helping.

---

### Post by Bachstelze on 2011-07-24
gmake is the name generally given to GNU make on non-GNU systems, because those systems generally have their own version of make, which works differently. Since Ubuntu is a GNU-based system, you should replace all occurrences of "gmake" in your script by just "make", or create a gmake symlink to make.

---

### Post by kelvin490 on 2011-07-25
> **Bachstelze said:**
> gmake is the name generally given to GNU make on non-GNU systems, because those systems generally have their own version of make, which works differently. Since Ubuntu is a GNU-based system, you should replace all occurrences of "gmake" in your script by just "make", or create a gmake symlink to make.
 
 
Thanks, but how to create a symlink? Is it in the script?

---

### Post by Bachstelze on 2011-07-25
```
cd /usr/bin
sudo ln -s make gmake
```

---


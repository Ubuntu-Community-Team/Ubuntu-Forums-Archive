---
title: "dpkg and finding files"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Mariane on 2008-11-02
Hi, 

I'm trying to compile something and I'm missing sys/malloc.h

It says "malloc.h" not found

I would like to install (or reinstall) it, but I don't know which package to install. 

How do I find out, please? 

I know "dpkg -L packagename" tells you where the package stuff is on the computer. Is there a way to use dpkg to ask it "what is the name of the package of which such a file is part?". 

Mariane

---

### Post by taurus on 2008-11-02
Are you trying to compile a c program with gcc?  If that's the case, then you need the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Mariane on 2008-11-03
Wrong package. To make sure I removed --purged it and then re-installed it, but I still get the same error message: sys/malloc.h file not found. 

Any other idea about where it might be, please? 

Mariane

---

### Post by conscious on 2008-11-03
I think it should be referred to as just <malloc.h>:
```
#include <malloc.h>
```

---

### Post by oldos2er on 2008-11-03
If you have build-essential installed, you'll find /usr/include/malloc.h

---


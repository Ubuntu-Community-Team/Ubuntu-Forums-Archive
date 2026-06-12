---
title: "gmp-devel"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by perito on 2008-10-08
I need to install gmp-devel (GNU Multiple Precision Arithmetic Library)
Im reading in the guide, just write
yum install gmp-devel

I cant run yum
   No module named cElementTree
...
how can i install that library?

---

### Post by Zhuang Tze on 2008-10-08
The correct command to run would be ```
sudo apt-get install libgmp3-dev
``` Most likely the guide you are following is for Fedora and not Ubuntu which is why it is telling you to use yum.

---

### Post by perito on 2008-10-08
thx a million
the guide also asks for
try running "yum install bzip2-devel" and/or "yum install zlib-devel"

how do i get these on ubuntu ?

---

### Post by Zhuang Tze on 2008-10-08
```
sudo apt-get install zlib1g-dev libbz2-dev
```

---

### Post by Absol on 2009-09-16
> **Zhuang Tze said:**
> The correct command to run would be ```
sudo apt-get install libgmp3-dev
``` Most likely the guide you are following is for Fedora and not Ubuntu which is why it is telling you to use yum.

Thanks a lot :D I also needed this

---


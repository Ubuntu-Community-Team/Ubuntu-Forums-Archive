---
title: "Where are the GNU libc man pages?"
date: 2007-05-29
forum: Programming Talk
---

### Post by balster neb on 2007-05-29
Hi,

I've being looking for the Ubuntu package that contains the man pages for the C standard library functions. I've used them with an older version of Ubuntu an year or two back, but I can't seem to find the appropriate package now. I'm looking for the man pages for C functions like printf(), fread(), etc.

I could look them up on one of many websites, but I strongly prefer having the man pages stored locally. :)

So far I've tried installing the seemingly obvious choices such as glibc-doc, but with no success.

I'm using Feisty Fawn, by the way.

---

### Post by ruy_lopez on 2007-05-29
```
sudo apt-get install manpages-dev
```

---

### Post by balster neb on 2007-05-29
> **ruy_lopez said:**
> ```
sudo apt-get install manpages-dev
```

Gah! That's it!

Silly of me for not finding it. Thanks a ton. :D

---


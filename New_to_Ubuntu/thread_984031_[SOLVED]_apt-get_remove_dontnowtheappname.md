---
title: "[SOLVED] apt-get remove dontnowtheappname"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-11-16
I want to remove a program, but I don't know it's name. I installed something a couple of months ago, that checks for application bugs when you update the system. I don't remember the software name. Does someone have any idea which program might be?

---

### Post by binbash on 2008-11-16
sudo apt-get remove apt-listbugs

---

### Post by kerry_s on 2008-11-16
> **binbash said:**
> sudo apt-get remove apt-listbugs

```
sudo apt-get remove --purge apt-listbugs
```

---

### Post by lovinglinux on 2008-11-16
Thank you.

---


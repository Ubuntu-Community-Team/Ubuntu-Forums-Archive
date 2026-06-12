---
title: "Screen Brightness Cannot Change"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by joseph6 on 2013-08-22
Hello,

I have been unable to change my screen brightness for several months now. It is always stuck on the highest setting, and it drains my battery. I can move the little meter to any position on the Brightness and Lock screen, but nothing actually changes, and when I click ok, still nothing happens. When I go back to the page, it has reset to max brightness. Any help would be appreciated, remember that I'm a novice when i comes to Ubuntu, so explain solutions in step by step instructions. Thanks!

---

### Post by sam_baker2 on 2013-08-22
joseph6, until someone can give you a more permanent solution, you might try this.
In the terminal paste this:

```
 xgamma -gamma .6
```

.6 may be to dark, so you may have to use something like 1.2 or 1.3
Experiment

---


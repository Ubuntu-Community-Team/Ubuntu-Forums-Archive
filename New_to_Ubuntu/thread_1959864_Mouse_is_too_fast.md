---
title: "Mouse is too fast"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by canam101 on 2012-04-16
I am running xubuntu 11.10. I was given an arc touch wireless mouse as a gift.

It works well but it is a bit too fast for me to be comfortable with it. I set the mouse parameters in the settings manager to be as slow as possible, but they did not slow it down enough.

Is there any sort of 'library' or utility available that  can be installed and will give better control over the mouse?

---

### Post by TeoBigusGeekus on 2012-04-16
Try with xset:
```
xset m x1 x2
```
x1: acceleration
x2: threshold

---


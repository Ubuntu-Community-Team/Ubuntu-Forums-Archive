---
title: "How to detect my secondary monitor?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-01
I have edited and added another monitor and screen in my xorg and I still cannot set the rez of my second display, when i click "detect displays" in screen resolutions nothing happens, what am I not doing here?

---

### Post by chewearn on 2008-05-02
What is your graphics GPU?  Intel, nvidia, ati, or some other?  If possible, include model number.

```
lspci | grep VGA
```

---


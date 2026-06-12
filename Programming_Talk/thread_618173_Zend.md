---
title: "Zend"
date: 2007-11-20
forum: Programming Talk
---

### Post by dc_jt on 2007-11-20
I have just downloaded Zend to Ubuntu and when I start it up, the tip box appears then when I close that all I get is a grey screen!!

The toolbar is not visible although it is actually there because I can use it using keyboard shortcuts, however whatever I do the screen just stays grey!!

By the way, the taskbar just says 'Java' rather than 'Zend Development Environment' which I think it should say.

Has this happened to anyone else? How do I fix?

Thanks

---

### Post by smartbei on 2007-11-20
It seems some people are javing issues with the GNU java binary and the solution is to install the Sun java runtime environment. No idea if this is the problem in your case. Anyway, try:
```

sudo aptitude install sun-java6-jre

```
With the multiverse repositories enabled.

If that command doesn't work, search for sun-java and install the one that looks like it :D.

---


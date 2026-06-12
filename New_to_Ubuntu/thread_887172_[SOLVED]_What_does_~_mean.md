---
title: "[SOLVED] What does ~/ mean?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Stan_1936 on 2008-08-11
I am trying to cleanup my desktop and found this command for opening up the necessary file.....this is in XFCE:
```
mousepad ~/.config/xfce4/desktop/xfdesktoprc
```

Question:  What does ~/ mean?

---

### Post by y@w on 2008-08-11
~ is used in *NIX operating systems as a variable for your home directory. On Ubuntu ~ for your user will usually be /home/<username>.

---

### Post by mc4100 on 2008-08-11
y@w explained it perfectly; for example, let's say your username is "stan"...
```
~/.config/xfce4/desktop/xfdesktoprc
```
really says,
```
/home/stan/.config/xfce4/desktop/xfdesktoprc
```

---

### Post by Stan_1936 on 2008-08-11
thanks, that answers the question.

---


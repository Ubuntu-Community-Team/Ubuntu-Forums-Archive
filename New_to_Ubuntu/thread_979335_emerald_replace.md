---
title: "emerald replace"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by lbarnes on 2008-11-11
hey guys, what's that emerald replace code to get emerald to work
i accidentally hit the default restore key in compiz
thanks

---

### Post by -Zeus- on 2008-11-11
```
emerald --replace
```

---

### Post by lbarnes on 2008-11-11
awesome, thanks
but it closes with the terminal
do i need to change the setting in window decoration in compiz?
do you know that command line?

---

### Post by adult swim on 2008-11-11
hit alt+F2 and type emerald --replace  there

---

### Post by lbarnes on 2008-11-11
i love this place

---

### Post by -Zeus- on 2008-11-11
> **lbarnes said:**
> awesome, thanks
but it closes with the terminal
do i need to change the setting in window decoration in compiz?
do you know that command line?

glad you love it.  pressing alt+f2 is easier, but if for some reason you need to use the console, try this:

```
emerald --replace &
```

The & tells it to keep running in the background, but you can't just hit the x button on the console.  You need to press Ctrl+D to quit, then it will keep running

---


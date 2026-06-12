---
title: "[SOLVED] Compiz-Help"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-04
I have compiz running but it has cut all the tops off my windows. How can I turn it off in terminal.

---

### Post by Canis familiaris on 2008-07-04
To disable compiz:
Alt + F2
```
metacity --replace
```

---

### Post by deadlySniper on 2008-07-04
Um yeah, it doesnt work, its says the command is not valid. I am using XUBUNTU

---

### Post by Canis familiaris on 2008-07-04
Sorry I thought you were using Ubuntu. This may help.
```
xfwm4 --replace
```

EDIT: Use Alt + F2, not terminal

---

### Post by deadlySniper on 2008-07-04
Thank you very much

---

### Post by dizee on 2008-07-04
xfwm4 --replace reverts to xfce instead of compiz.

to get compiz back but with a titlebar, run (alt+f2)
```
compiz --replace
```
then again press alt+f2 and run
```

gtk-window-decorator --replace
```
*or*
```
emerald --replace
```
emerald is the fancy window decorator, the other one is the default plain one.

ps good to see compiz installed for you.

---

### Post by Canis familiaris on 2008-07-04
> **dizee said:**
> 
then again press alt+f2 and run
```

gtk-window-decorator --replace
```
*or*
```
emerald --replace
```
emerald is the fancy window decorator, the other one is the default plain one.

I Didn't know that. Thanks. :)

---


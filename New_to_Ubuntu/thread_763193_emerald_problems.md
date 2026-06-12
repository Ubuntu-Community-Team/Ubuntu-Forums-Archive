---
title: "emerald problems"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by racgus on 2008-04-22
any idea as to why, when setting a new them through emerald, once i've entered into the terminal "emerald -- replace" the theme works, but once i've closed the terminal the theme goes away.

this happened to me on my desktop, but somehow it was fixed and haven't had the problem since, but now it is happening on my laptop. any thoughts?

---

### Post by bobbybobington on 2008-04-22
Try using this command in the terminal instead 
```
emerald -- replace &
```

---

### Post by Can+~ on 2008-04-22
Go to compiz-fusion advanced settings, decorations:

add the line "emerald --replace" into the "Command" and enable it, reload compiz if necessary.

---

### Post by racgus on 2008-04-22
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.


this is what i get everytime in terminal. if i exit terminal, the theme goes away with it. 

compiz config mgr. has window dec enabled as well. don't really understand what is going on here.

---

### Post by Moop on 2008-04-22
Install the fusion-icon from Synaptic. It's always worked good at sorting out the windows decorator. It's in the repos for hardy, not sure about other releases.

---

### Post by racgus on 2008-04-23
thanks, but that didn't seem to do the trick. i really don't know what i did differently with my desktop to where i have no problems with the emerald theme manager.

---

### Post by overdrank on 2008-04-23
> **racgus said:**
> thanks, but that didn't seem to do the trick. i really don't know what i did differently with my desktop to where i have no problems with the emerald theme manager.

HI and have you tried the alt, F2 keys then ```
emerald --replace
```

---

### Post by billgoldberg on 2008-04-23
You should really download the "compiz switch". It disables compiz fusion (and thus emerald) and then with another click it start compiz again (with the new emerald theme).

google for compiz switch for the .deb (you can add it to the panel for maximum effeciency)

---

### Post by racgus on 2008-04-24
> **overdrank said:**
> HI and have you tried the alt, F2 keys then ```
emerald --replace
```



WOW! virtual jumping high five to you sir! worked like a charm. how the easiest and simplest task is always the correct and most effective one. i have to get used to this linux concept.

---


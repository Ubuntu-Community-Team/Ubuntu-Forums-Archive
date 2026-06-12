---
title: "My Conky doesn't honour use_xft = true until I open and save it"
date: 2020-08-01
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-08-01
Hi everyone,

basically when I boot my computer, 99% of the time my Conky doesn't respect 'use_xft = true' and remains a small square in the corner of my desktop until I open my .conkyrc and save it again. All other configurations are applied. On an extremely rare occasion it will behave but I mean like extremely rare.

Any thoughts?

---

### Post by CatKiller on 2020-08-01
I've not seen that, but there have been things in the past where conky gets in a pickle because it's starting before the window manager has finished setting things up. The suggestion then is to stick a *sleep* for a few seconds in front of the command that launches conky.

---

### Post by deadflowr on 2020-08-01
Conky has built in pause option
Run something like
```
conky -p 20
```
Will delay from launching for 20 seconds.
If running conky with other option then just tack the -p at the end. 
something like
```
conky -c /this/that/theotherthing/conkyrc -p 20
```

---

### Post by jcdenton1995 on 2020-08-01
> **deadflowr said:**
> Conky has built in pause option
Run something like
```
conky -p 20
```
Will delay from launching for 20 seconds.
If running conky with other option then just tack the -p at the end. 
something like
```
conky -c /this/that/theotherthing/conkyrc -p 20
```

> **CatKiller said:**
> I've not seen that, but there have been things in the past where conky gets in a pickle because it's starting before the window manager has finished setting things up. The suggestion then is to stick a *sleep* for a few seconds in front of the command that launches conky.

Thanks to you both, I went with a simple... ```
/usr/bin/conky -p 2
```...which sorted it nicely, just because it's a Conky option.

---


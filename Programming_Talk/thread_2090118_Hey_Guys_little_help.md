---
title: "Hey Guys little help"
date: 2012-12-01
forum: Programming Talk
---

### Post by Mohan1289 on 2012-12-01
Hi guys in the screen shot that guy used a command

```

          ./test.shh 2>&1 |tee test.log

```

what's the use of 2>&1 and why he has to use that ??

---

### Post by steeldriver on 2012-12-01
```
2>&1
```redirects the standard error stream (stream 2) into the standard output stream (stream 1) - so error messages get combined with any other output from the command

---

### Post by zombifier25 on 2012-12-01
A little Googling gave me this:
[http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21](http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21)
Basically, 2>&1 means "redirect all output from stderr to stdout".
EDIT: Ninja'd!

---

### Post by Mohan1289 on 2012-12-01
> **zombifier25 said:**
> A little Googling gave me this:
[http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21](http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21)
Basically, 2>&1 means "redirect all output from stderr to stdout".
EDIT: Ninja'd!

Thanks

---

### Post by Mohan1289 on 2012-12-01
> **zombifier25 said:**
> A little Googling gave me this:
[http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21](http://stackoverflow.com/questions/818255/in-the-bash-shell-what-is-21)
Basically, 2>&1 means "redirect all output from stderr to stdout".
EDIT: Ninja'd!

Thanks Guys

---


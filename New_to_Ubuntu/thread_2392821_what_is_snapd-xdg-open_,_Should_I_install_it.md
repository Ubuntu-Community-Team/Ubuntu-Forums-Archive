---
title: "what is snapd-xdg-open , Should I install it ?"
date: 2018-05-25
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-05-25
So I want to install and use snaps.....I am wondering what snapd-xdg-open is...should I install it alongside snapd ?

---

### Post by kerry_s on 2018-05-25
why? xdg-open is part of ubuntu already.

[ATTACH=CONFIG]279855[/ATTACH]

---

### Post by PaulW2U on 2018-05-26
> **automate-stuff said:**
> So I want to install and use snaps.....I am wondering what snapd-xdg-open is...should I install it alongside snapd ?
You didn't say what version of Ubuntu you are using but from the terminal command:
```
apt show snapd-xdg-open
```
for Ubuntu 17.10 and later:
```
Description: Transitional package for snapd-xdg-open
 This is a transitional dummy package. It can safely be removed.

```
It probably had some use when snaps were first introduced but not now.

---


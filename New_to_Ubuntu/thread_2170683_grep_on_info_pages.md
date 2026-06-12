---
title: "grep on info pages"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by mikel2 on 2013-08-27
how do i use grep on  info pages i mean how i search particular line within all info pages. for example "foo" within the info ls info page

---

### Post by bkline on 2013-08-27
$ info ls 2>/dev/null | grep foo

The "2>/dev/null" bit is needed to suppress some extra diagnostic information emitted by info.

---

### Post by mikel2 on 2013-08-27
> **bkline said:**
> $ info ls 2>/dev/null | grep foo

The "2>/dev/null" bit is needed to suppress some extra diagnostic information emitted by info.

thanx

---

### Post by dnemcanin2 on 2013-08-27
use / for searching in info

example
info ls
then input / and type word you want to search
same is if you use less for reading file

---


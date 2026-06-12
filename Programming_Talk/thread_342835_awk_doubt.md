---
title: "awk doubt"
date: 2007-01-20
forum: Programming Talk
---

### Post by jordilin on 2007-01-20
in a portion of a larger script I have the following:
[CODE]var="$1"
awk -F : '/$var/ {print $5}' /etc/passwd

This does not work. I think the problem is in /$var/ how to include the value of the variable var inside the two slashes in awk. Anybody knows how to work around this?

---

### Post by ghostdog74 on 2007-01-20
awk has a -v option. you can use that to pass variables from the shell

---

### Post by jordilin on 2007-01-20
I have googled a bit and I've found that the solution is:
```
awk -F : /"$var" '/ {print $5}' /etc/passwd
```
Really weird, but it works,
thanks

---


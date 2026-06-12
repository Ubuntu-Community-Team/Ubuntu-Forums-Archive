---
title: "[SOLVED] bash if condition in /etc/init.d/rc"
date: 2008-10-13
forum: Programming Talk
---

### Post by lavinog on 2008-10-13
I was curious what the "." does in this if statement:
```
if [ "." = "$sh" ]
```

line 60 of /etc/init.d/rc

---

### Post by mssever on 2008-10-13
> **lavinog said:**
> I was curious what the "." does in this if statement:
```
if [ "." = "$sh" ]
```line 60 of /etc/init.d/rc
It's checking whether the value of $sh is a single dot. Nothing magic there. In bash tests, = means the same as == in many other languages.

---

### Post by lavinog on 2008-10-13
I see now. I overlooked the sh=. because it was commented out with the debian policy comment

All I was seeing was
```
sh=sh
if [ "." = "$sh" ] ; then

```
Which didn't make sense.
Thank you for the response.

---


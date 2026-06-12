---
title: "terminal command -r"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by konza on 2008-08-09
Running Hardy,  when i enter terminal command 'myname -r'  to find kernel version i get the return....
bash: xxxxx: command not found
What am i missing?

---

### Post by st33med on 2008-08-09
It is actually 'uname -r'

---

### Post by pikseli@work on 2008-08-09
It not supposed to do anything. Where did you get that idea?

try:

uname -r

---

### Post by Cope57 on 2008-08-09
```
man uname
```
for all the commands regarding uname.

---

### Post by wirelessmonkey on 2008-08-09
"myname" is not a valid command, I think you meant to use "uname -r" instead ;)

---

### Post by konza on 2008-08-11
Thanks to everyone.  Somehow i took "uname" as meaning to insert my user name...duh  Thanks again everyone.

---


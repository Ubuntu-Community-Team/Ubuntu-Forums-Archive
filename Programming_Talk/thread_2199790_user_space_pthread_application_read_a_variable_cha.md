---
title: "user space pthread application read a variable changed by kernel"
date: 2014-01-15
forum: Programming Talk
---

### Post by jwang36 on 2014-01-15
[COLOR=#333333]Hi, [/COLOR]

[COLOR=#333333]If I define a new variable in kernel (e.g. sched.c) codes, [/COLOR]
[COLOR=#333333]I want a user space thread (pthread) can read the value of this variable. [/COLOR]

[COLOR=#333333]What is the best way (faster and low overhead) to implement it,[/COLOR]
[COLOR=#333333]either creating a new /proc file or defining some system calls?[/COLOR]


[COLOR=#333333]Thanks, [/COLOR]

[COLOR=#333333]Jeff[/COLOR]

---


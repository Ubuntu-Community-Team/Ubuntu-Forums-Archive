---
title: "Help needed on how to debug &quot;segmentation fault&quot; of a python application &quot;gaupol&quot;"
date: 2007-01-11
forum: Programming Talk
---

### Post by 3togo on 2007-01-11
Gaupol is a very good subtitle editor for text-based subtitle files. However, gaupol crashed recently in Feisty.

As it is written in Python, I think it might not be very difficult to trace where the segmentation fault came from.

Unfortunately, I can't and I wonder any guru could help.


jc@jc-desktop:~$ gaupol
Segmentation fault
jc@jc-desktop:~$ sudo apt-cache search gaupol
gaupol - subtitle editor for text-based subtitle files
jc@jc-desktop:~$ sudo apt-get install gaupol

---

### Post by po0f on 2007-01-11
3togo,

```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install strace
$ strace gaupol[/FONT]
```

---


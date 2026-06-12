---
title: "PHP Segmentation Fault (core dump)"
date: 2007-09-11
forum: Programming Talk
---

### Post by md5hash on 2007-09-11
why is it that php 5.2.x produces segmentation fault (core dump) on linux
and php 5.1.4 on windows doesnt im testing the same scripts.

---

### Post by Lux Perpetua on 2007-09-11
Maybe because your code has a bug?

---

### Post by CptPicard on 2007-09-11
Either PHP sucks more than I had ever imagined or he deserves an award for creating an interpreted language bug that segfaults the interpreter :)

---

### Post by md5hash on 2007-09-11
> **Lux Perpetua said:**
> Maybe because your code has a bug?

the script runs fine on windows which has a lower version of php

---

### Post by Lux Perpetua on 2007-09-12
> **CptPicard said:**
> Either PHP sucks more than I had ever imagined or he deserves an award for creating an interpreted language bug that segfaults the interpreter :)I don't know of any such bug, but without seeing the code in question, that would be my wager. 

md5hash: code that works, or appears to work, can still be buggy. 

Of course, it's *possible* that you've uncovered a bug in PHP, but with the level of detail you're providing, we're never going to find out.

---

### Post by md5hash on 2007-10-09
im attaching the code here.. code executed via cron timer.

---

### Post by md5hash on 2007-10-13
bump.. anyone?

---

### Post by Lux Perpetua on 2007-10-13
Even people who are good at debugging code are going to have a hard time unless you tell them how to reproduce the crash or at least under what circumstances the script crashed. Be as specific as possible. If it's a bug in the interpreter and not in your code (unlikely, but possible), then of course, you're going to have to let people reproduce the crash.

---


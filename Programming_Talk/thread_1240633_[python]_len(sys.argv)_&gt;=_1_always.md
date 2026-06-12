---
title: "[python] len(sys.argv) &gt;= 1 always?"
date: 2009-08-14
forum: Programming Talk
---

### Post by ooobooontooo on 2009-08-14
Quick question. Is the following always greater than or equal to 1? Or are there special cases? This is python, but I would also appreciate an answer for other languages as well, like C.
> len(sys.argv)

---

### Post by snova on 2009-08-14
> **ooobooontooo said:**
> Quick question. Is the following always greater than or equal to 1? Or are there special cases? This is python, but I would also appreciate an answer for other languages as well, like C.

sys.argv[0] will be the name of the program (more specifically, the string by which the program was invoked), so it should always be at least one element long.

I have never known of a case where it might be missing. However, there seems to be something special about login shells, in that argv[0] has a **-** prepended to the command for some reason. I don't know how that works.

---

### Post by ooobooontooo on 2009-08-15
> **snova said:**
> sys.argv[0] will be the name of the program (more specifically, the string by which the program was invoked), so it should always be at least one element long.

I have never known of a case where it might be missing. However, there seems to be something special about login shells, in that argv[0] has a **-** prepended to the command for some reason. I don't know how that works.

I would guess the "-" has something to do with the standard input...though I'm not sure why it's there either... anyway, thanks for your answer. I was just double checking to make sure there weren't any weird cases with piping and stuff.

---


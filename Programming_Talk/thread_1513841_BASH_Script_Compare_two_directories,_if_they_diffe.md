---
title: "BASH Script: Compare two directories, if they differ, run code"
date: 2010-06-20
forum: Programming Talk
---

### Post by dmillerw on 2010-06-20
Title pretty much explains it all, basically trying to figure out how to compare dir1 to dir2, if dir2 is different from dir1, copy missing files...that at all possible?

Thanks in advance

---

### Post by Paddy Landau on 2010-06-20
Why not just copy the missing files?
```
cp --no-clobber dir1 dir2
```

---

### Post by dmillerw on 2010-06-20
I...did not know that command existed...thanks!

---

### Post by Paddy Landau on 2010-06-20
> **dmillerw said:**
> I...did not know that command existed...thanks!
The *man* command is your friend. I too did not know that the option existed until you asked the question.

I thought, "I wonder whether you can copy without overwriting?" I went to the terminal and entered:
```
man cp
```Nice 'n' easy. :)

---


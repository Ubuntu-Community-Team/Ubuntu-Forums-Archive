---
title: "help with bash variables?"
date: 2005-06-30
forum: Programming Talk
---

### Post by cannibalbob on 2005-06-30
I need a variable to = 001 NOT 1... so when i use N = `expr 001 + 1` it results as 002 NOT 2...
any ideas?
 :-?

---

### Post by LordHunter317 on 2005-06-30
You want to take 001 logical NOT 1?  That's 110... you need to give more information, I have no clue what you're even trying to attempt.

---

### Post by cannibalbob on 2005-06-30
no... not logic.  like this:

N=001
M=N+1

now M = 2 rather than 002...

---

### Post by LordHunter317 on 2005-06-30
Few ways you can do it:```
a=1
b=`expr $a + 1`
```If you want to be restricted to bash and most ksh shells, you can also say:```
a=1
b=$((a+1))
```

---


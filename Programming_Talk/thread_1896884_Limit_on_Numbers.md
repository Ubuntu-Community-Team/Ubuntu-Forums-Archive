---
title: "Limit on Numbers"
date: 2011-12-18
forum: Programming Talk
---

### Post by achuth on 2011-12-18
Is there any limit for the size of the number that I can use in an arithmetic operation in a shell script.
The following multiplication operation on very large numbers gives a negative sign also.


[I]Enter two numbers
3216549876545216
65478987931354666

Product is -3449254379524228224[/I]

I am using ubuntu 11.10.
If there exists a limit on the numbers, then what is it?

---

### Post by Bachstelze on 2011-12-18
Depends on the shell. Bash uses 64-bit integers (yes, even on 32-bit systems), so the range of values is -2^63 to 2^63-1.

*EDIT:* POSIX mandates that the precision of integers in sh be at least that of a C [font=monospace]long[/font], but allows higher precision.

---

### Post by MadCow108 on 2011-12-18
for arbitrary precision math use e.g. the *bc* program
```
res="`echo "3216549876545216*65478987931354666" | bc`"
echo $res
210616430546904539318302881577856

```
the output of this is a string so you do not have the integer limit problem (but also can't use it in bash internal arithmetic anymore)

---


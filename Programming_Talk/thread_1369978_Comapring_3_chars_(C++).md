---
title: "Comapring 3 chars (C++)"
date: 2010-01-01
forum: Programming Talk
---

### Post by qwertyuiop96 on 2010-01-01
I have the following code:

```
//Initialize 3 chars to same value
char c1 = 'x';
char c2 = 'x';
char c3 = 'x';

//Are the chars all equal to eachother?
if (c1 == c2 == c3) {
   return true;
} else {
   return false;
}
```

I would think the above code would return true, but it returns false.  Why?

---

### Post by MadCow108 on 2010-01-01
because of your condition, == is evaluated from left to right:
so first c1 == c2 returns true
then this is compared with the third:
true == c3
and this is false

do it like this:
if (c1 == c2 && c2 == c3 && c1 == c3)
you can skip the third if the comparison is transitive

compile with -Wall and you should get a warning about your dangerous condition

---

### Post by qwertyuiop96 on 2010-01-01
Yep , that was the problem.  Thanks!

---


---
title: "Sicp 1.10"
date: 2010-11-05
forum: Programming Talk
---

### Post by mo.reina on 2010-11-05
is it actually possible to evaluate the second expression by hand?  surely there must be a better way instead of substituting all the way down?  you'd need to use a whole wall to do it!

---

### Post by saulgoode on 2010-11-05
After you've completed the first expression, you should be able to determine the simple function (f y) which is equivalent to (A 1 y). 

Then when evaluating the second expression, don't expand out any of the steps when you encounter a (A 1 y); just evaluate y and afterward map it to (f y).

In other words, when the second expression is evaluated, the first substitution will result in (A 1 (A 2 3)). Noting that you've generically solved this expression, it is only necessary to evaluate (A 2 3) [and then substitute the result back into (f y)].

---


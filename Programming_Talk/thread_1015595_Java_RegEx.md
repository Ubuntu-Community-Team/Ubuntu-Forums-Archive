---
title: "Java RegEx"
date: 2008-12-19
forum: Programming Talk
---

### Post by DBQ on 2008-12-19
I am trying to match a pattern in Java of the form:

((a=b,b=c,d=e.......),(m=s,.....),(...))

ie. this pattern can repeat many times inside () (the a=b part).  I am trying to develop a RegEx for this.  How do I account for the repetition? It can repeat one times, 0 times, and any number of times.

Thank You.

---

### Post by slavik on 2008-12-19
something like:

"(\((\\w=\\w,?)*\),?)*"

* - 0 or more
? - 0 or 1
+ - 1 or more

---


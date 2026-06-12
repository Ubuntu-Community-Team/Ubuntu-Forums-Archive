---
title: "cout question"
date: 2007-01-28
forum: Programming Talk
---

### Post by Greykrrr on 2007-01-28
Hi, I am writing a small program in C++ to try and break one of the osix challenges. Now my question is how do I get the the program to output my result as one long number, instead of this: 7.01546e+012.

Thanks...

---

### Post by LotsOfPhil on 2007-01-28
[http://www.cplusplus.com/setprecision](http://www.cplusplus.com/setprecision)

I think that ought to do it. Just set the precision to 15 or something with larger than your exponent.

---

### Post by Greykrrr on 2007-01-28
Thanks! That did it exactly. 

Although my solution was of course still wrong but at least now it is not the fault of my program...

---


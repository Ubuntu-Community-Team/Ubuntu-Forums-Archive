---
title: "Arithmetic Test Operators"
date: 2011-12-18
forum: Programming Talk
---

### Post by achuth on 2011-12-18
Sir,
I use /bin/bash in my shell scripts.
For comparing two things I can use "=" sign as well as the "-eq".
Also for checking whether one value is greater than the other I can use ">" as well as the operator "-gt".

Is there any problem if I continue using the more familiar symbols like "=",">" while doing comparison operations? 
 
or...Is there any exclusive benefit in using the operators like "-eq", "-gt" etc ?

---

### Post by MadCow108 on 2011-12-18
both types of operaters do different things
= < > etc are string operators
-eq -gt -lt etc are integer operators

it gets even more complicated because what they do also depend on what construct you use to compare [[]] vs (())
see:
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

---

### Post by Bachstelze on 2011-12-18
And this is why I hate shell scripting. :p

---


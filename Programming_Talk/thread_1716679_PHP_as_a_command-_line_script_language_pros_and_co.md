---
title: "PHP as a command- line script language: pros and cons?"
date: 2011-03-28
forum: Programming Talk
---

### Post by varelov on 2011-03-28
A rather general question regarding scripting: what would be pros and cons for using PHP as a scripting language, over say bash or Perl scripting?
Why would you use PHP for system scripts and when would you not?

---

### Post by kurum! on 2011-03-28
> **varelov said:**
> A rather general question regarding scripting: what would be pros and cons for using PHP as a scripting language, over say bash or Perl scripting?
Why would you use PHP for system scripts and when would you not?


Pros:

1) PHP already comes with a lot of libraries that makes things easier 
2) Your script is Portable. PHP scripts can be run on Windows etc...(with the windows version of PHP of course)
3) Standardization. 

Cons:
1) depends on the system problem to solve, for example, parsing huge files. Sometimes using PHP would be slower, than for example, using awk.

Overall, there's nothing wrong with using PHP as a system admin scripting language. Just preferences.

---


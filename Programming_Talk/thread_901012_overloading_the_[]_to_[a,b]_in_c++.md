---
title: "overloading the [] to [a,b] in c++"
date: 2008-08-26
forum: Programming Talk
---

### Post by monkeyking on 2008-08-26
Hi does anyone know if it si possible in c++ to overload the subscript operator [],
in such a way, that the user, can supply 2 args in the []. 

thanks in advance

---

### Post by CptPicard on 2008-08-26
No, not like that it is not possible. However you can construct something like x[a][b], or overload () which seems to be recommended here:

[http://www.parashift.com/c++-faq-lite/operator-overloading.html#faq-13.10](http://www.parashift.com/c++-faq-lite/operator-overloading.html#faq-13.10)

---


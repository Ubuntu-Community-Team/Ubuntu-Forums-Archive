---
title: "Someone explain ::new c++"
date: 2013-03-18
forum: Programming Talk
---

### Post by akvino on 2013-03-18
[PHP]
void 
construct(pointer __p, const _Tp& __val)                                                                                                  &#9474;
 { ::new((void *)__p) _Tp(__val); } 
[/PHP]

Taken out of std::queue. What does ::new or exactly :: do in this syntax?

---

### Post by pbrane on 2013-03-18
Basically **::** in this case means to use the current namespace **new** as opposed to one that may have been defined in the std::queue class. I think :: is called the scope resolution operator.

---


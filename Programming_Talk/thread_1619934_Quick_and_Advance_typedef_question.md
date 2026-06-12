---
title: "Quick and Advance typedef question"
date: 2010-11-12
forum: Programming Talk
---

### Post by akvino on 2010-11-12
Can someone explain this syntax? PRIHashItem is a class?
typedef Hashint32<PRIHashItem, int>* HashPtr;

---

### Post by worksofcraft on 2010-11-12
Hashint32 is evidently a template combining that class and an int as well and then your HashPtr type is being defined to point to one of these.

---

### Post by akvino on 2010-11-12
> **worksofcraft said:**
> Hashint32 is evidently a template combining that class and an int as well and then your HashPtr type is being defined to point to one of these.

I just came to the same conclusion and was able to look up .h file for it. 
It is a template....

---


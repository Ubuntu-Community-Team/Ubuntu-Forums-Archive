---
title: "Scheme String (or quoted) manipulation"
date: 2008-12-31
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-31
I need to be able to split apart quoted stuff charecter by charecter
[PHP]
(char '?a 0) --> '?
(char '?a 1) --> 'a
(char '?asd 2) --> 's
[/PHP]

---

### Post by Mr.Macdonald on 2008-12-31
If this isn't possible please tell me too!

---

### Post by CptPicard on 2009-01-01
On MIT Scheme, check out the symbol->string function which returns a string representation of the symbol. Then just handle that string normally to extract characters.

---


---
title: "Quick C++ vector question"
date: 2010-02-10
forum: Programming Talk
---

### Post by kahumba on 2010-02-10
Hi,
Trying to properly clean up a vector which contains pointers to a class "File".
The site at
[http://www.cplusplus.com/reference/stl/vector/clear/](http://www.cplusplus.com/reference/stl/vector/clear/)
says the vector method "clear()" before removing its elements calls their [COLOR=#000000][FONT=Times New Roman][FONT=verdana]destructors[/FONT][/FONT][/COLOR], however in my case their destructors don't get called.

Is that cause I'm using pointers to elements instead of elements or is it something else?

---

### Post by SledgeHammer_999 on 2010-02-10
> **kahumba said:**
> Is that cause I'm using pointers to elements instead of elements or is it something else?

Yes. The "element" the vector holds is a pointer-to-object not the object itself. You have to manually "delete" each pointer before clear()

---

### Post by kahumba on 2010-02-10
thanks

---


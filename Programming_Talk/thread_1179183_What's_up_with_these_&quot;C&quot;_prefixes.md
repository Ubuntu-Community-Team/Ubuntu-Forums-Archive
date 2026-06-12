---
title: "What's up with these &quot;C&quot; prefixes?"
date: 2009-06-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-06-05
Half of source files in LieroX got this weird prefix, like CInput.h, CMap.h, CChatBox.h etc.

Other games/programs got those prefixes too. Why is that? What is that C supposed to mean? Client? Core?

Edit: Quake doesn't have those prefixes. It's just c++ stuff.

---

### Post by simeon87 on 2009-06-05
Class, most likely.

---

### Post by x33a on 2009-06-05
in c++, headers such as cstdlib, mean c++ version of the c headers such as stdlib.h.

i cannot say if it stands true for the games too.

---

### Post by nvteighen on 2009-06-05
Er... and how can that detail be important, I ask?

---

### Post by Reiger on 2009-06-05
Prefixes like that are often used to create ad-hoc namespace convetions especially in languages which do not sport formal namespace declarations... 

But sometimes the same thing is done to link various items that 'belong' together without being in the same class/namespace whatever: essentially the concept of Hungarian notation. Things prefixed the same `do the same kind of thing'. Useful if you have for instance relative and absolute offsets to be calculated relative or absolute to a Window pane (and not a conceptual 3D coordinate system): you could have WOffset() and COffset() to denote the conceptual difference.

---


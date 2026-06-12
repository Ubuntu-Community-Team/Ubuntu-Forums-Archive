---
title: "is this declaration valid  ? (java)"
date: 2008-06-28
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-28
my friend has got some strange questions in his mind...or maybe he borrows from the internet ..
is this declaration valid ?
static int volatile const x = 10;

---

### Post by Phristen on 2008-06-28
const is not used in java, use final instead... Not in this case though because if it's final, it can't be volatile.
And also, all the modifiers must go before the type, so correct declaration would be
static volatile int x = 10;

---

### Post by dexter.deepak on 2008-06-28
thanks...and sorry for that const instead of final...am playing with cpp these days.

---

### Post by Jordanwb on 2008-06-29
Plus finals are by default static if memory serves me right.

---


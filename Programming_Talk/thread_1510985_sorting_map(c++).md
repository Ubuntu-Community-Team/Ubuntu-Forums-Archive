---
title: "sorting map(c++)"
date: 2010-06-16
forum: Programming Talk
---

### Post by bahador.saket on 2010-06-16
Dear All

I have some characters and also some numbers related to these characters.
for example:

input:
A--->1
B--->3

I stored them in a map, how can I sort them in a same time?
 
output:
A---->1
B---->3
C--->4

Cheers,
Bahador

---

### Post by Zugzwang on 2010-06-16
Do you want to sort by the map key or the map value (i.e., by the character or by the number)?

---

### Post by bahador.saket on 2010-06-16
both of them because the number of characters is important for me.
I want to sort character and number together in the same time.

---

### Post by Zugzwang on 2010-06-16
> **bahador.saket said:**
> both of them because the number of characters is important for me.
I want to sort character and number together in the same time.

Hmmm, this hardly makes sense for a map (or I don't get it correctly). So you want to sort lexicographically (look it up on Wikipedia if you don't know the term) by the (key,value) pair. However, as the keys are unique, the value will never be taken into account.

---

### Post by DanielWaterworth on 2010-06-16
I'd make 2 maps, one either way and 2 sets, then write a class to handle the insertions and deletions. This can then handle any use case you can think of.

---

### Post by simeon87 on 2010-06-16
> **DanielWaterworth said:**
> I'd make 2 maps, one either way and 2 sets, then write a class to handle the insertions and deletions. This can then handle any use case you can think of.

That could be more complex than needed.

Is the sorted list (it must be an ordered datastructure, which a map is not necessarily) needed a lot? The simplest thing is to, when requested, create a list and fetch the values in the desired order (i.e., 'A', 'B', ..., 'Z').

---


---
title: "Design Problem"
date: 2009-08-19
forum: Programming Talk
---

### Post by uljanow on 2009-08-19
hi,
how would you solve a problem in which you need to make an object X available to a container T or it's elements of type E **without** 

[LIST]
[*] modifying the container
[*] introducing a global variable
[*] synchronizing static variables (T and E have to be thread-safe)
[*] increasing the size of an element object
[*] using thread-local storage
[/LIST]

It looks almost impossible.

---

### Post by Lux Perpetua on 2009-08-19
What do you mean by "make available"? How is X to be used by T & E?

---

### Post by uljanow on 2009-08-20
Object X should be accessible through the container or elements. It's basically data that all elements share. But I'd like to avoid the overhead of synchronisation or additional space requirements.

The container is passed to a callback function as an argument.

---


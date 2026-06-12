---
title: "dynamic two dimentionnal array of an object in c++ best way?"
date: 2011-02-06
forum: Programming Talk
---

### Post by gufide on 2011-02-06
Hi, anyone know the best way to make a dynamic two dimentionnal array of an object? I need to do some change like resizing in columns and in row...

---

### Post by worksofcraft on 2011-02-06
> **gufide said:**
> Hi, anyone know the best way to make a dynamic two dimentionnal array of an object? I need to do some change like resizing in columns and in row...
In C++ you can use [std::vector]("http://www.cplusplus.com/reference/stl/vector/") which automatically allocates extra memory as you add to it.

If you make a vector of vectors then you have the equivalent of a 2D array that has the built in capability to expand and contract both in rows and columns.

---

### Post by gufide on 2011-02-06
I will try to found a good tutorial... thank you!

---

### Post by jakewan on 2011-02-06
Scott Meyers' _Effective STL_ is very good.

---

### Post by worksofcraft on 2011-02-06
If you need to do rapid row and column insertions and deletions
but you don't mind allocating for the worst case to start with then it is more efficient to set up a single vector of row pointers and a single vector of column indexes.

These are used to access in a large memory space that you allocated for the total. Then all you have to do to delete/insert a whole row or column is to update one of those two vectors.

A lot depends on what you really want to use it for: are you trying to economize on memory used, on individual object access times or on speed of row/column insertions and deletions?

---


---
title: "join 2 files"
date: 2008-02-28
forum: Programming Talk
---

### Post by davidtuti on 2008-02-28
Hi,

In ksh how could I join 2 files:

for instanace:

file1:
------
me llamo
direccion
codigo postal

file2:
-----
david
calle pepe
28000

As result:

file3:
------
me llamo david
direccion calle pepe
codigo postal 28000

Thanks a lot and sorry for my english

---

### Post by ruy_lopez on 2008-02-28
```
paste file1 file2 > file3
```

---

### Post by davidtuti on 2008-02-28
Thanks a lot

:):):)

---


---
title: "Increaze Wine drive size"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by kraziyk on 2012-06-04
So I am trying to install EVE Online, which is almost 19 GB. My wine file is 12.5 GB. Obviously I don't have enough space. But I don't know how to create a new wine file or parition or what ever the wine setup is technically. 

Does anyone know how I can set up Wine with more than the 12.5 GB of space?

Thanks for the help.

---

### Post by ubudog on 2012-06-04
As far as I know, the .wine directory is like any other directory on the system, and can grow as needed.

Someone please correct me if I am wrong.

---

### Post by idoitprone on 2012-06-04
> **ubudog said:**
> As far as I know, the .wine directory is like any other directory on the system, and can grow as needed.

Someone please correct me if I am wrong.

yep it occupies

$HOME

or the home of the user.

if your home partition is filled, then you starting deleting files or moving them.

---

### Post by Perfect Storm on 2012-06-05
clean the trash can ;)


On the second note; If you have a spare partition or HDD you can set up a /games partition and then move .wine to it. Then symblink it to your home directory.

---

### Post by carl4926 on 2012-06-05
I think the OP is confused.
Probably the Ubuntu install is a minor one, with little dedicated space.

---


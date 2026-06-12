---
title: "Execute a linux command based on inserts into a mysql table"
date: 2007-03-14
forum: Programming Talk
---

### Post by thusi02 on 2007-03-14
Hi, 

I was wondering if anyone out there knows of a way to run a linux command/script based on if data is inserted into a mysql table. 

Cheers, 
Nathan.

---

### Post by blanky on 2007-03-14
Well, you could probably write a program that checks the database at a set interval, and then executes the information in the database accordingly.

---

### Post by elst on 2007-03-15
Look into "triggers", a standard database feature which runs code when a condition occurs. Older versions of MySQL didn't support this feature.

---


---
title: "How to tar a .gz folder"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ben22 on 2008-05-05
Hi,

I uploaded a .sql dump of a DB and need to extract it.

However ```
tar -zxvf file.sql.gz
``` is not working.

which is the correct command?

thx,
Ben

---

### Post by Monicker on 2008-05-05
.gz usually just denotes gzip. .tar.gz is for a file that was tarred and gzipped.


Try

gunzip file.sql.gz

---

### Post by ben22 on 2008-05-05
> **Monicker said:**
> .gz usually just denotes gzip. .tar.gz is for a file that was tarred and gzipped.


Try

gunzip file.sql.gz

not working, the error is still the same

"not in gzip format"

---

### Post by Monicker on 2008-05-05
> **ben22 said:**
> not working, the error is still the same

"not in gzip format"

What is the output of the following command?

file file.sql.gz

---


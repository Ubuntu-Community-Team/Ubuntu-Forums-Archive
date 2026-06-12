---
title: "Search for file type without extension"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by KaliVoid on 2008-04-26
hello

lets say i want to find all the picture _type_ files in the system
(jpg,bmp,gif...)but not all of the files have extension.

how can i find them all in one Go ?  (terminal & GUI)

Tnx

---

### Post by kidders on 2008-04-27
Hi there,

One way might be to try something like...```
find / -type f -exec file -i {} \; | grep "image/"
```
Something like that could take a *very* long time to execute though ... it analyses the MIME type of every single file on your entire system, and spits out the ones that have "image/" in them (eg "image/jpeg", "image/x-photoshop", etc.). That way, even if you called a PNG "image" ... or even "image.xls" ... it'll be found.

Hopefully you'll only need to run something like that on your home directory, and not your whole system.

---

### Post by KaliVoid on 2008-04-27
hi

thanks a lot , very helpful and educational :)

thanks agin

---


---
title: "Please help in using dd command"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by karthikbalaji on 2008-05-16
Hi All,

I have a disk dump of size 1000 MB. I want to skip the first 64kb of this dump and create a new dump.

I tried 

dd if=dump1.dmp of=dump2.dmp bs=1024 skip=64kB .But it is not giving the expected result.

Please tell me the correct way of doing it.

Thanks,
Karthik.

---

### Post by karthikbalaji on 2008-05-16
It worked when i specified it in no of blocks..

64k accounts to 128 blocks

dd if=dump1.dmp of=dump2.dmp bs=1024 skip=128 worked fine..

---


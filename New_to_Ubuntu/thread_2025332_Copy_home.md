---
title: "Copy /home"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by smemamian on 2012-07-14
hi 

How do I copy the contents of /home ?
/picture , /video and  all, to, For example /usr/myfolder

---

### Post by Old_Grey_Wolf on 2012-07-14
```
cp -r /home/myfolder /usr/myfolder
```

---

### Post by BBQdave on 2012-07-14
> **smemamian said:**
> How do I copy the contents of /home ?
/picture , /video and  all, to, For example /usr/myfolder

If you are using Unity, you can simply drag and drop to myfolder.

If you are using a CLI (command line interface), you can use the command **cp** **-r** /home/myhome /backup/myhome

For more information on **cp**, from a CLI type **info cp** :)

---

### Post by smemamian on 2012-07-14
tnx

---


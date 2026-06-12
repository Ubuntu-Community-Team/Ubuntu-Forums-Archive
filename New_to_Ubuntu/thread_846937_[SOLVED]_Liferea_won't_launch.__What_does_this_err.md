---
title: "[SOLVED] Liferea won't launch.  What does this error mean?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by crjackson on 2008-07-02
Every I launch Liferea news reader, it opens then closes quickly.  I've removed it, deleted configuration files, reinstalled it.  It would work fine for a few hours then back to the same error.  Can someone help me fix this please?

I opened in terminal and this is the error:
```
charles@charles-laptop:~$ liferea
Obtaining the module object from Python failed.

Traceback (most recent call last):
cant import cStringIO
<type 'exceptions.ImportError'>: /usr/lib/python2.5/lib-dynload/time.so: undefined symbol: PyExc_ValueError

Liferea did receive signal 11 (Segmentation fault).
charles@charles-laptop:~$ 
```

---

### Post by Club17 on 2008-07-02
I have the same trouble, Liferea 1.4.16 won't launch, but with different code:

```
c17@Athlon64-u8:~$ liferea

** ERROR **: Failure while preparing statement, (error=1, table itemsets has no column named parent_node_id) SQL: "INSERT INTO itemsets (item_id,parent_item_id,node_id,parent_node_id,read,comment) VALUES (?,?,?,?,?,?)"
aborting...
Aborted
c17@Athlon64-u8:~$ 

```

Anybody have a solution?

Thxxx!

---

### Post by crjackson on 2008-07-02
> **Club17 said:**
> I have the same trouble, Liferea 1.4.16 won't launch, but with different code:

```
c17@Athlon64-u8:~$ liferea

** ERROR **: Failure while preparing statement, (error=1, table itemsets has no column named parent_node_id) SQL: "INSERT INTO itemsets (item_id,parent_item_id,node_id,parent_node_id,read,comment) VALUES (?,?,?,?,?,?)"
aborting...
Aborted
c17@Athlon64-u8:~$ 

```

Anybody have a solution?

Thxxx!

Glad I'm not the only one.  I was considering reinstalling my OS from scratch.

---

### Post by aeiah on 2008-07-02
from a quick scan it seems its got a bug and has been fixed. either install an older version or install 1.4.16b

>         Version 1.4.16b (Stable) 

        * Fixes SF #1990601: schema creation bug introduced 
          in 1.4.16. Only affects first installations. 
          (reported by Yaakov Selkowitz) 

---

### Post by cendant on 2008-07-02
Or give up Liferea totally and try the wonderful RSSOwl

[http://www.rssowl.org](http://www.rssowl.org)

---

### Post by crjackson on 2008-07-02
> **cendant said:**
> Or give up Liferea totally and try the wonderful RSSOwl

[http://www.rssowl.org](http://www.rssowl.org)

I'm not a big fan of java apps.  I'll wait until the fixed version hits getdeb.  Thanks

---


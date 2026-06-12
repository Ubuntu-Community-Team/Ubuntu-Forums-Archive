---
title: "What is the package for mysql C connector?"
date: 2013-01-30
forum: Programming Talk
---

### Post by luckyisdog on 2013-01-30
I couldn't find the name anywhere, I've tried various installs of some other mysqls but it didn't quite get mysql.h my_global.h my_sys.h. Which one did you guys use for a quick installion of the connector?

---

### Post by spjackson on 2013-01-30
libmysqld-dev

---

### Post by luckyisdog on 2013-01-31
Ah still doesn't work on Eclipse. Added the library mysql.


Should I remove all other MySQL packages before installing this one?

---

### Post by spjackson on 2013-01-31
> **luckyisdog said:**
> Ah still doesn't work on Eclipse. Added the library mysql.

With libmysqld-dev installed, a command line to build a simple test is:
```

gcc mytest.c -o mytest -I/usr/include/mysql -lmysqlclient

```
How that translates into Eclipse, I'm not so sure.
> 
Should I remove all other MySQL packages before installing this one?
No.

---

### Post by luckyisdog on 2013-01-31
Oh so it uses the library mysqlclient? Alright I will try that. Thanks for your help! One question: can I still use this c library for c++ or is there a specific library?

---

### Post by luckyisdog on 2013-02-01
Ahh got some problems including mysql.h my_global.h my_sys.h turns out that I needed to include them last because it looked like vector and fstream class were having problems with my_global.h weird.

Anyways it's working now. Thanks a lot for your help!

---


---
title: "MySQL expire datas"
date: 2011-01-29
forum: Programming Talk
---

### Post by The_Aegidius on 2011-01-29
Is there any option to auto-delete some rows with some values, after some time in a MySQL database?

---

### Post by slavik on 2011-01-29
only if you track additions with a timestamp and have a scheduled job to do it.

---

### Post by The_Aegidius on 2011-01-30
I found [this]("http://dev.mysql.com/doc/refman/5.0/en/triggers.html"), but I realize that the best way to do it, in my case, is with a PHP script.

Anyway, thanks for helping.

---


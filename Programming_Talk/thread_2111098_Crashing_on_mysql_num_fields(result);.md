---
title: "Crashing on mysql_num_fields(result);"
date: 2013-02-01
forum: Programming Talk
---

### Post by luckyisdog on 2013-02-01
Just created a new database and made a table named players.

so mysql_query works mysql_store_result works but when the line of execution hits:
num_fields = mysql_num_fields(result);

then it crashes!

anyone know why? Maybe it's a new table with no data in so it can't retrieve num_fields?

---

### Post by luckyisdog on 2013-02-01
Actually performing wrong queries!

---


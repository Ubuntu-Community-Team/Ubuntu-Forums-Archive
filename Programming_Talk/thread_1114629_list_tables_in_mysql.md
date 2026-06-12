---
title: "list tables in mysql"
date: 2009-04-03
forum: Programming Talk
---

### Post by sulekha on 2009-04-03
Hi all,


How to get the list of tables in mysql from a particular database based on engine type(MyISAM,InnoDB,MERGE,HEAP,BDB etc) ?

---

### Post by sujoy on 2009-04-03
SHOW TABLE STATUS FROM [name of database];

or better yet

$ mysql -u username -p -e "SHOW TABLE STATUS FROM database_name" | awk '{print $1, $2}'|column -t

---


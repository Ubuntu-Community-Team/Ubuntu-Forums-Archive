---
title: "how to pass PL/SQL-BOOLEAN argument to procedure in Oracle using python"
date: 2008-06-26
forum: Programming Talk
---

### Post by mystic-d on 2008-06-26
hey
im using cx_Oracle to connect my python code to Oracle database,
and i wanted to know how can i pass PL/SQL-BOOLEAN argument to procedure ?
my code is something like "cursor.execute(query,varList)"
where query is "begin SYS.MYPACKAGE.MYPROCEDURE(varcharArg => :1,booleanArg => :2); end;"
and varList is my argument list, and the second argument need to be of type BOOLEAN, how can i achive that ?
thanks !

---


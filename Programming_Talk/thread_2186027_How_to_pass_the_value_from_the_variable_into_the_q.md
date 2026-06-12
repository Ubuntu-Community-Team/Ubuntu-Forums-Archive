---
title: "How to pass the value from the variable into the query"
date: 2013-11-05
forum: Programming Talk
---

### Post by marcofsportugal on 2013-11-05
[C Programming Language]

I've been try to perform the following query:

```

scanf("%32s", &user); (...)
if(mysql_query(conn,"SELECT password From user where username='admin'"))

//where you see 'admin' should be the value of the variable user
```

how to pass the value from the variable* user *into the query?
Ty guys!

---

### Post by QIII on 2013-11-05
*Moved to **&#8203;Programming Talk***

---

### Post by Bachstelze on 2013-11-05
1. Do not use scanf().
2. Essentially, you want something like
```

char query[SOME_SIZE];
sprintf(query, "SELECT password From user where username='%s'", user);
mysql_query(conn, query);

```
but you have some input sanitisation to do. Since I am not a MySQL expert, I will leave this to others.

---

### Post by ofnuts on 2013-11-05
Use "prepared statements"?

---

### Post by r-senior on 2013-11-07
> **ofnuts said:**
> Use "prepared statements"?

+1

Concatenating strings to form queries means the database has to parse the SQL multiple times, which is an unnecessary overhead. With a prepared statement the query is parsed once and the variable is bound at execution time.

Here is an example in C/MySQL:

[http://lgallardo.com/en/2011/06/23/sentencias-preparadas-de-mysql-en-c-ejemplo-completo/](http://lgallardo.com/en/2011/06/23/sentencias-preparadas-de-mysql-en-c-ejemplo-completo/)

---


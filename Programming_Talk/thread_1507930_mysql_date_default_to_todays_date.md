---
title: "mysql date default to todays date"
date: 2010-06-12
forum: Programming Talk
---

### Post by ja660k on 2010-06-12
Hey all.

I want to know how to add todays date in SQL as the default for a column?

my sql looks like:
```


mysql> create table users(
    -> id int not null primary key,
    -> name varchar(50) not null,
    -> address varchar(50) not null,
    -> phone varchar(9) not null default "0000-0000",
    -> lastLogin date default curdate()
    -> );

```
and the error
```

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'curdate()
)' at line 6
mysql> 

```
i know its giving me a syntax error, but how can i get that to work?

---

### Post by Compyx on 2010-06-12
MySQL doesn't support function calls as default values, only constants. However, for this particular problem, you can change the field type to 'TIMESTAMP':

```

create table users(
    -> id int not null primary key,
    -> name varchar(50) not null,
    -> address varchar(50) not null,
    -> phone varchar(9) not null default "0000-0000",
    -> lastLogin **timestamp default current_timestamp**
    -> );

```

The TIMESTAMP field has the same representation as a DATETIME field. You can also have the field automatically update on UPDATE queries by adding 'ON UPDATE current_timestamp' to the field declaration.

More information can be found here: [http://dev.mysql.com/doc/refman/5.0/en/timestamp.html]("http://dev.mysql.com/doc/refman/5.0/en/timestamp.html")

Hope this helps.

---


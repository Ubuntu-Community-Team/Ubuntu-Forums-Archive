---
title: "Setting the active database using mysql C API"
date: 2011-02-04
forum: Programming Talk
---

### Post by guest_user on 2011-02-04
how do I set the active database after logging in:

mysql_real_connect( conn, "localhost", "username", "password", NULL, 0, NULL, 0 );
mysql_query( conn, "create database test" );

after this, now that the database is created, how can I set the active database to be test?

---

### Post by slavik on 2011-02-04
> **guest_user said:**
> how do I set the active database after logging in:

mysql_real_connect( conn, "localhost", "username", "password", NULL, 0, NULL, 0 );
mysql_query( conn, "create database test" );

after this, now that the database is created, how can I set the active database to be test?
Answer: [http://dev.mysql.com/doc/refman/5.0/en/mysql-change-user.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-change-user.html)

---

### Post by MadCow108 on 2011-02-04
I guess select_db is what op wants:
[http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html)

---

### Post by guest_user on 2011-02-04
> **MadCow108 said:**
> I guess select_db is what op wants:
[http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html)

yup but my concern is whether is it deprecated?

---

### Post by slavik on 2011-02-04
> **MadCow108 said:**
> I guess select_db is what op wants:
[http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-select-db.html)
I fail at reading :(

---

### Post by MadCow108 on 2011-02-04
> **guest_user said:**
> yup but my concern is whether is it deprecated?

I see no indication that it is deprecated.

mysql_create_db is deprecated but not mysql_select_db
[http://dev.mysql.com/doc/refman/5.5/en/mysql-create-db.html](http://dev.mysql.com/doc/refman/5.5/en/mysql-create-db.html)

you can also use mysql_query with a "use test" to select the database

---

### Post by guest_user on 2011-02-05
thank you

---


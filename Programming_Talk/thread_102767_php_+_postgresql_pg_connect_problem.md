---
title: "php + postgresql pg_connect problem"
date: 2005-12-12
forum: Programming Talk
---

### Post by goneskiing on 2005-12-12
I am having trouble connecting php(5.1.1) and postgresql(8.1).  Both run fine separately.  I get the following error using pg_connect:

Warning: pg_connect() [function.pg-connect]: Unable to connect to PostgreSQL server: FATAL: Ident authentication failed for user "tempuser" in /var/www/db_connect.php on line 14

The line 14 is the pg_connect statement: pg_connect(dbname=tempdb user=tempuser).  

If I run psql -l it shows the database "tempdb" with the username "tempuser".  Now I did not create a password when I created the user and in pg_connect just use the dbname and username values - is that a problem?  thanks.

---

### Post by ph0x on 2005-12-13
I'd try with something like
```

passwd=""

```


greetz ph0x

---

### Post by goneskiing on 2005-12-13
thanks for the suggestion, but it did not work.  Are there other ways to test ?

---

### Post by goneskiing on 2005-12-13
okay - fixed.  Solution was to change the pg_hba.conf file for local operation

---

### Post by schmidty on 2006-02-03
Thanks for the fix...I was wondering if this issue would cause a problem if you were going to run a server using PHP5, PostgreSQL 8 and Apache2 in cyberspace? Anyone know the answer?

Schmidty

---


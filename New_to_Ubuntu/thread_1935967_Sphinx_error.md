---
title: "Sphinx error"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-03-05
HI,

While running the following command
**  "/opt/lampp/htdocs/workspace/wp/wp-content/uploads/sphinx/bin/indexer    --rotate  --config  /opt/lampp/htdocs/workspace/wp/wp-content/uploads/sphinx/sphinx.conf  wp_delta wp_main wp_stats" **

in terminal i get the error

ERROR: index 'wp_stats': sql_connect: Can't connect to local MySQL  server through socket '/var/run/mysqld/mysqld.sock' (2)  (DSN=mysql://root:***@localhost:3306/wp).

Kindly help me to solve this error

---

### Post by ubudog on 2012-03-05
Is your MySQL server running?

Do: 
```
ps ax | grep -i sql
```

Do you see something like: 
```
17736 ?        Ssl   16:50 /usr/sbin/mysqld
```

---

### Post by pmohankumar on 2012-03-07
Output i got:

3776 ?        S      0:00 /bin/sh /opt/lampp/bin/mysqld_safe --datadir=/opt/lampp/var/mysql --pid-file=/opt/lampp/var/mysql/TP771.pid
 3902 ?        SNl    0:05 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --log-error=/opt/lampp/var/mysql/TP771.err --pid-file=/opt/lampp/var/mysql/TP771.pid --socket=/opt/lampp/var/mysql/mysql.sock --port=3306
 9042 pts/0    S+     0:00 grep -i sql

---


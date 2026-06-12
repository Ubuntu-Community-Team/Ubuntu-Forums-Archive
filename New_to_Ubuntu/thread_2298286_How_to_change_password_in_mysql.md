---
title: "How to change password in mysql"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by houmingc on 2015-10-09
Today in ubuntu, mysql can't log in. Why?

ubuntu@ubuntu-UX32VD:~$ mysql -u root -r
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

On one terminal i did
         > sudo service mysql stop
         > sudo mysqld --skip-grant-tables
On another terminal
         > mysql -u root -r
         > UPDATE user SET Password=password('root') where user='root';
         > ERROR 1046 (3D000): No database selected.    <what should i do next>

---

### Post by QIII on 2015-10-10
Hello!

When you use --skip-grant-tables, you should be able to get into mysql like this:

```
mysql -u root
```

and then do the UPDATE like this:

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('SomeNewPassword');
```

or, for 5.7.6 or later

```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'SomeNewPassword';
```

Last, flush privileges:

```
mysql> FLUSH PRIVILEGES;
```

By the way, [this]("https://dev.mysql.com/doc/refman/5.7/en/index.html") might be helpful for future reference.

---


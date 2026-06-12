---
title: "installing the PDO MySQL extension"
date: 2012-06-14
forum: Programming Talk
---

### Post by anon0 on 2012-06-14
Hi all, I have a basic question on MySQL:

[http://de.php.net/manual/en/ref.pdo-mysql.php](http://de.php.net/manual/en/ref.pdo-mysql.php)
"Use --with-pdo-mysql[=DIR] to install the PDO MySQL extension, where the optional [=DIR] is the MySQL base install directory."

Which file should be used for that command?

edit: think it's mysql, but I'm getting "Access denied for user 'root'@'localhost' (using password: YES)". Trying to look that up...

---

### Post by wallaroo on 2012-06-15
No I believe it's a PHP config setting when compiling PHP.

But if you install the 'php5-mysql' module through the 'Package Manager', it should include the mysql PDO libraries.

To check that the mysql PDO support is installed, type the following in a terminal ..

```
php -i|grep PDO
```
If support is installed you should see something like this ..
```
PDO
PDO support => enabled
PDO drivers => mysql
PDO Driver for MySQL => enabled

```

---

### Post by anon0 on 2012-06-15
Thanks, I noticed it was already enabled.

---


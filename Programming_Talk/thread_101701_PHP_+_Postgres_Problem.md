---
title: "PHP + Postgres Problem"
date: 2005-12-10
forum: Programming Talk
---

### Post by gruszczy on 2005-12-10
I'm trying to use postgres database in my php application, but I get an error on the first command - pg_connect(). Is there anyone, who installed it and have it working, and could help me with it? The dbms, apache and php works fine, I simply cannot to the database via php.

---

### Post by invalid on 2005-12-10
What is the exact error?

---

### Post by gruszczy on 2005-12-10
```
Fatal error: Call to undefined function: pg_connect() in /var/www/usos/logowanie.php on line 7
```

And the php code:

```
<body>
	<?php
		$database = pg_connect("dbname=usos");
```

I have some question too - do I have to be logged to the database, while trying to reach it via php? 

In /etc/php4/apache2/php.ini I added this line
```
extension=pgsql.so
```

Any idea, what might be wrong?

---

### Post by invalid on 2005-12-10
Do you have the php-pgsql package installed?

---

### Post by gruszczy on 2005-12-10
I did everything as it is written here [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) , except for the fact, that I didn't isnstall mySQL. Therefore I assume, that I didn't install php-pgsql package. How should I do it? ```
 sudo apt-get install php-pgsql 
``` is enough?

---

### Post by invalid on 2005-12-10
```
sudo apt-get install php4-pgsql
```
or replace 4 with 5, if that is what you are using.

Be sure to restart apache after you get it installed.

---

### Post by gruszczy on 2005-12-10
OK, i'll try it. Thank you very much, I really appreciate your help.

I found what caused the error. Now everything works fine. Once again: thanks.

---

### Post by schmidty on 2006-02-21
What was the solution to your problem?
I am having the same problem...

Schmidty

---

### Post by dbarbour on 2006-03-01
Yes, installing the php5-pgsql package solves the problem.```
apt-get install php5-pgsql
```As stated, be sure to restart Apache.```
/etc/init.d/apache2 restart
```

---


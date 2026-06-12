---
title: "PHP and Mysql Beginner"
date: 2007-07-03
forum: Programming Talk
---

### Post by questpro on 2007-07-03
Hi, I have just started learning PHP and MySql.  I installed apache http server, php5, mysql using the ubuntu guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

When I tried to connect to the database following error message is generated -
```

Hello World
Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'admin'@'localhost' (using password: YES) in /var/www/firstphp.php on line 6
could not connectAccess denied for user 'admin'@'localhost' (using password: YES)
```

I browsed through previous posts here to rectify the problem but not succeeded. Any help is appreciated, Thank you very much.

And I used the following code.

```
<?php

echo "Hello World";

if (mysql_connect("localhost","admin","1admin")){
	echo "Connected Succesfully";
	}
	else{
	die ('could not connect' . mysql_error());
	}

?>
```

Please reply. Thanks

---

### Post by Bachstelze on 2007-07-03
Are you sure about your MySQL login info ?

---

### Post by runningwithscissors on 2007-07-03
You need to create the user you're trying to access the db with in the mysql users table, and give it the appropriate permissions.

To lean how:
[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

---

### Post by questpro on 2007-07-03
Do I need to set the user name and the password before?

---

### Post by kosmic on 2007-07-03
Do you have any user Created in MySQL called "admin" ?

---

### Post by Bachstelze on 2007-07-03
> **questpro said:**
> Do I need to set the user name and the password before?

If you haven't already, run 

```
sudo mysql_secure_installation
```

To setup a password for your MySQL root account. You can then use it to login *via* PHP.

---

### Post by questpro on 2007-07-03
Thanks a lot for the quick responses. I got it now.

---


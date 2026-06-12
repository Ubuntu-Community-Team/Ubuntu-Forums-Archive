---
title: "Unable to link PHP code to MySQL?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-20
sorry, i know that this is probably the wrong place to put this,  but it's really the only forum that i know of...

Anyway, If you think that this is the totaly wrong place to put this, then please suggest a different forum to put this post, Thank you


Ok, here is my problem, this is the PHP code that i have

[php]
<?
$user="justin";
$password="password";
$database="contacts";
mysql_connect(localhost,$user,$password);
@mysql_select_db($database) or die( "Unable to select database");
$query="CREATE TABLE contacts (id int(6) NOT NULL auto_increments,first varchar(15) NOT NULL,last varchar(15) NOT NULL,phone varchar(20) NOT NULL,mobile varchar(20) NOT NULL,fax varchar(20) NOT NULL,email varchar(30) NOT NULL,PRIMARY KEY (id),UNIQUE id(id), key id_2 (id) )";
mysql_query($query);
mysql_close();
?>
[/php]

Ok, im trying to learn MySQL and PHP, so this is the example they gave at this website
[http://www.freewebmasterhelp.com/tutorials/phpmysql/2](http://www.freewebmasterhelp.com/tutorials/phpmysql/2)

The Output i get when i try to display this page in my web browser (firefox) is 
> 
**Fatal error:**Call to undefined funtion mysql_connect() in /var/www/test2.php on line 4


So this would lead me to belive that my login is somehow wrong...
But i think i have it correct... I created a database in the mysql client with the 
> create database contacts;[quote]
and got
[quote]Query OK, 1 row affected (0.00 sec)[quote]

and i think that my login and password are correct cause when i type this, i get the following

[quote]
justin@localhost:`$mysql
ERROR 1045 (28000): aCCESS DENIED FOR USER 'justin'@'localhost' (using password: NO)
justin@localhost:`$mysql -p
Enter password:
Welcom to the MySQL monitor. ect....


Help is greatly appreciated!

---

### Post by scragar on 2008-10-20
You are doing this on a local host then you will need to install the php5-mysql package in order to use mysql functions.
```
sudo apt-get install php5-mysql
```

And perhaps programming talk would have been a better choice?

---

### Post by justinram22 on 2008-10-20
ehh, i installed the packages you suggested

> 
sudo apt-get install php5-mysql


but still the same error.....

Help is greatly appreciated, and i can't thank you enough for my last post help

---

### Post by scragar on 2008-10-20
ok, try installing:
```
libapache2-mod-auth-mysql
```eg:
```
sudo apt-get install libapache2-mod-auth-mysql
```
And restart apache when that's done:
```
sudo /usr/sbin/apache2ctl stop
sudo /usr/sbin/apache2ctl start
```

---

### Post by justinram22 on 2008-10-20
Thank you again!!!!!!!!!!! how do you thank someone?

---

### Post by scragar on 2008-10-20
bottom right of the post, funny little icon:[img]http://ubuntuforums.org/images/buttons/post_thanks.gif[/img]

---


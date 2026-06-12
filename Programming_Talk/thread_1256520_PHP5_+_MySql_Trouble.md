---
title: "PHP5 + MySql Trouble"
date: 2009-09-02
forum: Programming Talk
---

### Post by anitagraser on 2009-09-02
Hi all!

I'm having trouble getting php5 + mysql work.

I installed apache2, libapache2-mod-php5, php5, php5-mysql, mysql-server following the instructions on ubuntuusers.de

phpinfo() doesn't show anything concerning mysql except for this line:

additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini

MySQL is running and I can easily access it via MySQL Administrator.

Trying to connect php to mysql fails:

$con = mysql_connect("localhost","user","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

**Fatal error: Call to undefined function mysql_connect() in /home/anita/public_html/guestbook/guestbook.php on line 13**

I tried adding

extension=mysql.so

to /etc/php5/apache2/php.ini, but it didn't help.

Any help would be appreciated

---

### Post by pnewbie on 2009-10-16
HI, 
 I am also facing the same error. Iam still working on it. You can use this link ..... i don't know if it will help you ???? any how if you have already solved this your problem kindly tell me how you have done it....
 
[http://dev.mysql.com/doc/refman/5.4/en/mysql-real-connect.html](http://dev.mysql.com/doc/refman/5.4/en/mysql-real-connect.html)
 
Bye and take care

---

### Post by korvirlol on 2009-10-17
> I installed apache2, libapache2-mod-php5, php5, php5-mysql, mysql-server following the instructions on ubuntuusers.de

Did you install libapache2-mod-php5 or libapache2_mod-php5. if you installed them all in one line, you would probably not notice an error. The "underscored" library is the correct one

---

### Post by pnewbie on 2009-10-18
install this seprately:
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql

You can read from here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)



Bye and tc

---

### Post by januzi on 2009-10-19
> **anitagraser said:**
> 
I tried adding

extension=mysql.so

to /etc/php5/apache2/php.ini, but it didn't help.

Did You "/etc/init.d/apache2 restart" after that change ?

---


---
title: "PHP configuration problems"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-25
I installed the server edition 8.04 as a LAMP. I have managed to get my web development pages from my windows XP system and can view them through LocalHost in my browser. I have some PHP pages that will not execute that work under Windows XP/Apache Server . I go to the adept package manager and PHP5-common, PHP5-Mycrypt, PHP5-MySQL, is installed. I have tried creating the PHPinfo() test page saved as phpinfo.php with the following code.

<?php
phpinfo();
?> 


Saved in the same directory as my other web pages. When I try to view this in my browser I get a downloads page when I click on the phpinfo.php file it goes to a launch application dialog page. When I pick choose an application to run this file it goes to a file tree there is nothing there to run the PHP script.  Anybody have any suggestions on something I'm missing or maybe a guide for further testing and getting this to work? Something is not configured correctly.  All help will be appreciated.

---

### Post by drubin on 2008-10-25
> **JKHinton CPBD said:**
> and PHP5-common, PHP5-Mycrypt, PHP5-MySQL, is installed.

You seem to have left off. libapache2-mod-php5

Take a look here
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by JKHinton CPBD on 2008-10-26
Hey drubin,

Thank you very much for the response.  I had found out about the 
libapache2-mod-php5 and made sure it was loaded.  I had not found the guide link that was a big help, I ran the a2enmod php5 
and then the sudo /etc/init.d/apache2 restart command and this got my phpinfo() code to run php scripts. I am still having trouble connecting to MySQL database where the passwords and usernames are located.  Maybe some more digging in the quide will reveal.  Anyway thanks again for the quick and useful response.

James in GA,USA

---

### Post by drubin on 2008-10-26
> **JKHinton CPBD said:**
> Hey drubin,

Thank you very much for the response.  I had found out about the 
libapache2-mod-php5 and made sure it was loaded.  I had not found the guide link that was a big help, I ran the a2enmod php5 
and then the sudo /etc/init.d/apache2 restart command and this got my phpinfo() code to run php scripts. I am still having trouble connecting to MySQL database where the passwords and usernames are located.  Maybe some more digging in the quide will reveal.  Anyway thanks again for the quick and useful response.

James in GA,USA

Default username/password for mysql is  
Username: **root**  EDIT: way to many o's :) 
Password: there isn't one just put a blank string.

[Changing default password]("http://www.mydigitallife.info/2006/06/06/change-and-reset-mysql-root-password/")

---


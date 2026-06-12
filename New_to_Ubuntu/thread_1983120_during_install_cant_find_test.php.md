---
title: "during install cant find test.php"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-19
Hi all

I have been installing Apache, php and mysql on my machine from instructions:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
I have successfully setup Apache and have installed php. The instructions state that:
> 
Checking PHP 5 installation 
In  /var/www , create a text file called "test.php", grant the world (or,  at least, Ubuntu user "apache") permission to read it, write in it the  only line: "<?php phpinfo(); ?>" (without the quotation marks)  then, with your web browser, go to the URI "[http://localhost/test.php](http://localhost/test.php)": if you can see a description of PHP5 configuration, it proves PHP 5 works with Apache. 
So I created test.php in my /var/www directory and chmod the file:
```

glenn@acer:/var/www$ ls -al
total 16
drwxr-xr-x  2  root     root       4096 May 19 21:14 .
drwxr-xr-x 14 root     root       4096 May 19 20:52 ..
-rw-r--r--      1  root      root      177 May 19 20:52 index.html
-rw-r--r--      1  www-data www-data   20 May 19 21:14 test.php
-rw-r--r--      1  root     root        0 May 19 21:14 test.php~
glenn@acer:/var/www$ 

```but when I goto [http://localhost.test.php](http://localhost.test.php) it gives me a 404 not found error.

Any suggestions?

---

### Post by Cheesemill on 2012-05-19
You've typed the wrong URL. It should be:
[http://localhost/test.php](http://localhost/test.php)

---

### Post by Senior_Buckethead on 2012-05-19
> **Cheesemill said:**
> You've typed the wrong URL. It should be:
[http://localhost/test.php](http://localhost/test.php)

OOps...But still did not fix the problem. Still have a 404 error.

---

### Post by hannysabbagh on 2012-05-19
follow the  images and save you IP number:
 [[IMG]http://helal.is-sec.org/wiki/lib/exe/fetch.php?w=200&media=screenshot_from_2012-05-16_17_32_38.png[/IMG]]("http://helal.is-sec.org/wiki/lib/exe/fetch.php?media=screenshot_from_2012-05-16_17_32_38.png") 
  [[IMG]http://helal.is-sec.org/wiki/lib/exe/fetch.php?w=200&media=screenshot_from_2012-05-16_17_33_02.png[/IMG]]("http://helal.is-sec.org/wiki/lib/exe/fetch.php?media=screenshot_from_2012-05-16_17_33_02.png") 

now open your firefox, write your ip and your file name,E.X: 192.168.1.4/test.php , did that worked?
thanks

---

### Post by Senior_Buckethead on 2012-05-19
My arabic is a bit rusty....

[http://192.168.1.65/test.php](http://192.168.1.65/test.php)

Yeah Nah didn't work. Apache is set up as localhost so should work as [http://localhost/test.php](http://localhost/test.php)

> 
**Installing PHP 5**

 To only install PHP5. use [any method]("https://help.ubuntu.com/community/InstallingSoftware") to install the package 

libapache2-mod-php5Enable this module by doing 
sudo a2enmod php5which creates a symbolic link  /etc/apache2/mods-enabled/php5 pointing to  /etc/apache2/mods-availble/php5 . 
Except  if you use deprecated PHP code beginning only by "<?" instead of  "<?php" (which is highly inadvisable), open, as root, the file  /etc/php5/apache2/php.ini , look for the line "**short_open_tag**  = On", change it to "short_open_tag = Off" (not including the quotation  marks) and add a line of comment (beginning by a semi-colon) giving the  reason, the author and the date of this change. This way, if you later  want some XML or XHTML file to be served as PHP, the "<?xml" tag will  be ignored by PHP instead of being seen as a PHP code mistake. 
Relaunch Apache 2 by 
sudo service apache2 restart 
**Checking PHP 5 installation**

 In  /var/www , create a text file called "test.php", grant the world (or,  at least, Ubuntu user "apache") permission to read it, write in it the  only line: "<?php phpinfo(); ?>" (without the quotation marks)  then, with your web browser, go to the URI "[http://localhost/test.php](http://localhost/test.php)": if you can see a description of PHP5 configuration, it proves PHP 5 works with Apache.



---

### Post by hannysabbagh on 2012-05-19
open terminal and write:
[B][I]sudo apt-get install mysql-server mysql-client apache2 php5  libapache2-mod-php5 php5-mysql php5-curl php5-gd php5-intl php-pear  php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps  php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc  php5-xsl phpmyadmin

[/I][/B] /etc/init.d/apache2 restart 



big things but it is better then nothing :) now do it agian and write your ip in your firefox, e.g 192.168.1.4 will something like that appear to you:
 [[IMG]http://helal.is-sec.org/wiki/lib/exe/fetch.php?media=1.png[/IMG]]("http://helal.is-sec.org/wiki/lib/exe/fetch.php?media=1.png")
thx

---

### Post by Senior_Buckethead on 2012-05-19
Nope, that doesnt work. Basically you have just told me to reinstall everything that I already have installed.
And, the command /etc/init.d/apache2 restart 
needs to be:
sudo /etc/init.d/apache2 restart 

Yes, I can find localhost on my browser. But that wasn't the problem. Getting the configuration information for the php install to display, which is invoked by the php instruction 
```

<?php phpinfo(); ?>

```
 in the file test.php.

For some reason the browser either can't find, or can't read the file test.php, is the problem.

---

### Post by Senior_Buckethead on 2012-05-19
These instructions from 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> 
In  /var/www , create a text file called "test.php", grant the world  (or,  at least, Ubuntu user "apache") permission to read it, write in it  the  only line: "<?php phpinfo(); ?>" (without the quotation  marks)  then, with your web browser, go to the URI "[http://localhost/test.php](http://localhost/test.php)": if you can see a description of PHP5 configuration, it proves PHP 5 works with Apache.
Don't create a file called test.php in /var/www. Create a file called test.php with the following code:
```

<html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html>

```And save it in your ~/public_html folder which you created as part of installing Apache2, which is located in your home directory.

and display it by running in your browser [http://localhost/test.php](http://localhost/test.php).

Its should work. It has for me.

---

### Post by jjz on 2012-05-27
I have a similar problem. Terminal message for sudo a2enmod php5 tells me Module php5 already enabled. I've created files test.php, info.php and phpinfo.php, with correct syntax, both as just <?php phpinfo(); ?> and with html head and body tags, in my public_html folder. When however I try to access them in a browser, the browser downloads the files rather than opening them. Can someone help me work out what I'm doing incorrectly? I read above about making files accessible--perhaps I need to do that? If so how would I make the file accessible to apache2?

---

### Post by Senior_Buckethead on 2012-05-27
Ok, forget about php for a second. When you enter http:\\127.0.0.1 or http:\\localhost you should get a page in your browser with 'It works!' or "it is working' displayed. Mine says '[B]Hello! It is working!'.
[/B]Does yours do that? If so Apache is working (I think..).

From: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> 
Does your browser ask if you want to **download the php** file instead of displaying it?  If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5.  It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. 
Maybe you should purge and then reinstall a2enmod php5.

Do you know how to do that?

If it still doesn't work then start another thread in absolute beginners. You'll get better help than anything I can do.

---

### Post by jjz on 2012-05-27
Thanks for your time and help, Senior_Buckethead. Yes, I could view the test page just fine. Good news, I've just found the solution--I needed to comment out some lines in the config file. Done that and it's working beautifully now.

---

### Post by Senior_Buckethead on 2012-05-27
Good to know. Happy php'ing.

Glenn.

---

### Post by adglife on 2012-10-05
> **jjz said:**
> Thanks for your time and help, Senior_Buckethead. Yes, I could view the test page just fine. Good news, I've just found the solution--I needed to comment out some lines in the config file. Done that and it's working beautifully now.

Which config file? I'm having the exact same problem, and am lost.

---


---
title: "Unable to work on PHP"
date: 2006-12-02
forum: Programming Talk
---

### Post by SwaroopKunduru on 2006-12-02
Hi All,

I used synaptic manager to install PHP. I selected PHP and other related processes and loaded(installed) them and I wanted to work on it I can't see where it is installed. 

Please help with steps to install and work on PHP.

Thanks in advance,

Swaroop Kunduru.

---

### Post by Ramses de Norre on 2006-12-02
PHP isn't a program you can start, it's a kind of scripting language to render websites. So to use it you'll need to write a php script in a text editor and save it as index.php in the root of a webserver (e.g. apache which is in the repos) and then open the page in a webbrowser.

There are plenty of tutorials on php scripts on the net, do a search through google or something to find out more.

---

### Post by SwaroopKunduru on 2006-12-02
Hi Ramses de Norre's ,

Thanks for your time to answer my question. I went to [www.w3schools.com](www.w3schools.com) and copied PHP scripts in html code and named the file as index.php. I am using Tomcat to deploy, in tomcat webserver webapps I created the webapplication structure and stored this index.php.

The page when deployed it was O.K but when I called from browser I got a blank screen. 

There is something I am missing in PHP, is it a PATH or LIB Path? I don't know. Some one Please help.

Thanks in advance.

Regards,

---

### Post by Verminox on 2006-12-03
You have to put your PHP scripts in your web document root.

eg. If you have Apache installed, find the 'htdocs' directory and put all your PHP scripts in there... and access them via [http://localhost](http://localhost).

I have XAMPP installed so I don't know where the directory would be if you got Apache through apt. For me it is /opt/lampp/htdocs.

---

### Post by adamkane on 2006-12-03
LAMP (aka PHP) allows you to install a CMS, which are these great web portals to giant apps that allow you to manage lots of data/information:
[http://www.opensourcecms.com/](http://www.opensourcecms.com/)

Here's all you need to get LAMP to work with a CMS:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

-----------------------------------------------------------------------------

For Apache2/PHP-latest/MySQL-latest, install XAMPP:
[http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

---

### Post by Verminox on 2006-12-03
> **adamkane said:**
> _LAMP (aka PHP)_ allows you to install a _CMS_, which are these great web portals to giant apps that allow you to manage lots of data/information:
[http://www.opensourcecms.com/](http://www.opensourcecms.com/)


LAMP is not an alias for PHP. It stands for Linux, Apache, MySQL and PHP.

Also, installation of any of these "services" has nothing to do with a CMS.... a CMS is just a web application usually working with PHP/MySQL.

---

### Post by SwaroopKunduru on 2006-12-03
Hi All,

Thankyou to all of you for spending your time.

I gave the command and got the result below.

swaroop@swaroop-laptop:~$ sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
Password:
Reading package lists... Done
Building dependency tree... Done
php5 is already the newest version.
mysql-client-5.0 is already the newest version.
mysql-server-5.0 is already the newest version.
E: Couldn't find package phpmyadmin
swaroop@swaroop-laptop:~$


Please let me know what should I do to fix it.

Regards,

Swaroop Kunduru.

---

### Post by pmasiar on 2006-12-06
> **Verminox said:**
> LAMP is not an alias for PHP. It stands for Linux, Apache, MySQL and PHP.

Not exactly. P stands for: PHP, Perl, or Python :-)

---

### Post by Wim Sturkenboom on 2006-12-07
How do you want to use PHP? For a webserver or for plain scripting (both is possible).

Let's assume webserver.

> **SwaroopKunduru said:**
> 
E: Couldn't find package phpmyadminYou normally don't need that package for a webserver.

Once everything is installed (and it seems to be), start your browser and connect to [http://localhost](http://localhost). You should see some apache information.
Does it work?
If so, create a file phpinfo.php containing the following code:[PHP]<?php
phpinfo();
?>[/PHP]and store it in the webserver document root (I use slackware as a webserver and don't know where the default webserver document root is in Ubuntu).
In the browser, use the url *[http://localhost/phpinfo.php](http://localhost/phpinfo.php)*
You should now see information about PHP.
Does it work?

If something does not work, tell us where it fails and someone can point you in the right direction.

---


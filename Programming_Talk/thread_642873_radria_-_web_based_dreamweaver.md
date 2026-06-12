---
title: "radria - web based dreamweaver"
date: 2007-12-17
forum: Programming Talk
---

### Post by suoko on 2007-12-17
In order to install it you must have apache2, php and mysql installed
Afterwards...

- sudo aptitude install php5-curl php5-gd 
- sudo /etc/init.d/apache2 restart
- copy radria files to /var/www/radria ([http://radria.sqlfusion.com/download.php](http://radria.sqlfusion.com/download.php))
- cd /var/www/radria/SiteManager
- sudo chown -R www-data tmp/ package projects config.php radria_run.log radria_error.log
- go to [http://localhost/radria](http://localhost/radria)

go to packages and install what you need

---

### Post by Vadi on 2007-12-17
Hm, I got a whole lot of errors:


> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'root'@'localhost' (using password: YES) in /var/www/radria/RadriaCore/class/mysql/sqlConnect.class.php on line 163
(sqlConnect) : Database Connect Error : Couldn't connect to the database Wrong login and password or Wrong host name
Warning: Cannot modify header information - headers already sent by (output started at /var/www/radria/RadriaCore/class/mysql/sqlConnect.class.php:163) in /var/www/radria/SiteManager/includes/i18n.postconf.inc.php on line 12
	

New 	 
Open 	 
Settings 	
FTP setup 	

Upload
	
Packages 	
Help
webide
		
	
Tools
Preview Project
Logs
	
		
- 	
Your project Project is now open.
You can use the tools on the left to work on it or install additional packages to your project.

The default username / password are the same as the database access of the project, if you didn't setup a database they are admin / sqlfusion.

You will find more information and help at: Radria.org documentation


Radria SiteManager 4.0, Copyright SQLFusion LLC 2002-2007


I did set a password on mysql, but radria never asked for it... where can I put it in?

---

### Post by plewicki on 2007-12-19
Actually you need one more step.

Its to run the install setup wizard that will check the required extensions and set the database.
[http://localhost/radria/SiteManager/install.php](http://localhost/radria/SiteManager/install.php)

The install script just check the current php system and set the database connexion.

You can setup the database connexion manually in:
radria/SiteManager/config.php

For configuration and installation you can check out the documentation at:
[http://radria.sqlfusion.com/documentation/radria_installation]("http://radria.sqlfusion.com/documentation/radria_installation")

---

### Post by Vadi on 2007-12-19
> WARNING: .htaccess not executed by apache
In your apache configuration authorize apache to read and execute .htaccess. This is not required but many external packages and application uses .htaccess file for authentication and url rewriting.
For that you can add in your apache configuration:

<Directory "/var/www/radria/SiteManager">
AllowOverride all
</Directory>

Does it want me to put that in to apache2.conf that's in /etc/apache2 ?

---

### Post by plewicki on 2008-01-07
May be not exactly, depend on your existing configuration and file path.

The .htaccess execution is used by some package to rewrite urls or set local php variables.
Its not required but helps make things simple.

For improved security you can move all the .htaccess contents in your apache configuration and keep the override to none.

---


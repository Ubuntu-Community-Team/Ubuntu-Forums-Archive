---
title: "SQL with Ubuntu"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-06-11
Hello, im wounder if there is any program in ubuntu that can make me work on sql but offline i mean to see my work like webpages (blog) fist then to publish it later. any idea?

---

### Post by mike_g on 2008-06-11
mysql is the open source version. For a blog I'd recommend wordpress. It comes with mysql apache and the other bits and pieces you would you need for a blog. You can get it through apt:
```
sudo apt-get install wordpress
```
Then type 'localhost' into your url to test that its working.

---

### Post by Ginoxy on 2008-06-11
Thanks, i did that but where can i find the program?

---

### Post by Ginoxy on 2008-06-11
Any idea where can i find "wordpress" ?

---

### Post by KingTermite on 2008-06-11
> **Ginoxy said:**
> Any idea where can i find "wordpress" ?

Some programs don't automatically put themselves in the menu. You may have to go to Applications->Add/Remove and find it to add it to menu.

---

### Post by Ginoxy on 2008-06-11
i did that, but seems like wordpress is not there !

---

### Post by ad_267 on 2008-06-11
It's not there, it isn't an application in the usual sense. It's a web application. Type in [http://localhost](http://localhost) in your web browser. You may need to go to [http://localhost/wordpress](http://localhost/wordpress) or something. Have a look in /var/www, this is where your web pages are for your web server.

Wordpress is software for writing a blog and you use it in your web browser. You can have it installed on your own computer for testing but usually it is installed on a web server and you log in to your website to edit your blog.

---

### Post by Ginoxy on 2008-06-12
okay its not working ! i mean nothing there ! i looked into ver/www and the only file there is index.html ?

---

### Post by lazyart on 2008-06-12
Community docs for wordpress:

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by Ginoxy on 2008-06-12
Thanks a lot , 

now i have this problem 

404 Not found
Warning: require_once(/etc/wordpress/config-localhost.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 16

Fatal error: require_once() [function.require]: Failed opening required '/etc/wordpress/config-localhost.php' (include_path='.:/usr/share/php:/usr/share/pear') in /etc/wordpress/wp-config.php on line 16

any idea?

---

### Post by cpetercarter on 2008-06-12
Once you have Apache, php and mysql installed on your computer (see [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") for help on how to do this), the easiest way to install Wordpress or any other php web application is to do it in exactly the way you would if you were installing it on a remote web server. Download the WordPress zip file from the Wordpress site; create a new directory (wordpress) in your "localhost" root (/var/www unless you have changed it to somewhere else); unzip the WordPress zip file to this directory; open a browser, navigate to [http://localhost/wordpress/wp-admin/install.php](http://localhost/wordpress/wp-admin/install.php) and follow the instructions. 

Apart from WordPress, I have installed phpmyadmin and LoudBlog in this way. For some applications, eg LoudBlog, you need to create a new mysql database before you run the install programme.

---

### Post by Ginoxy on 2008-06-12
I did exactly what you mentioned but still have some problems  

check this 
[ATTACH]73857[/ATTACH]

---

### Post by ad_267 on 2008-06-12
Well what does your wp-config.php file say? Is the mysql username and password correct? Have you started mysql?

Can you create a file called testphp.php and put that in /var/www and in that file put this:

```
<?php phpinfo() ?>
```

Then browse to that file and post what you see here. Check that there is a section on MySQL

---

### Post by Ginoxy on 2008-06-12
i dont know !

when i log to [http://localhost/wordpress](http://localhost/wordpress) 

it gives me this 

Error establishing a database connection

---

### Post by ad_267 on 2008-06-12
Sorry, I edited my post. 

Can you do this: 

Can you create a file called testphp.php and put that in /var/www and in that file put this:

```
<?php phpinfo() ?>
```

Then browse to that file and post what you see here. Check that there is a section on MySQL

---

### Post by Ginoxy on 2008-06-13
i created that file , how to browse it? and how can i be so sure to run mysql ?!

---

### Post by ad_267 on 2008-06-13
If the file is at /var/www/testphp.php then you can browse to it by going to [http://localhost/testphp.php](http://localhost/testphp.php)

That file will have a section on mysql if everything has been set up correctly.

---

### Post by Ginoxy on 2008-06-13
Seems like nothing there? now i did something wrong ;/ 
by mistake i deleted wordpress by rm -rf wordpress 

how can i get it back?

---

### Post by cariboo on 2008-06-13
A much easier way to check if mysql is running in a terminal type:

```
mysql -u <username> -p <password>
```

Where <username> is the your  mysql user name and <password> is your mysql password. 

If that  gives you an error message similar to this:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

then mysql is not running

---

### Post by Ginoxy on 2008-06-13
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

that what it gives me !!!

---

### Post by ad_267 on 2008-06-13
> **Ginoxy said:**
> Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

that what it gives me !!!

Well that's good. That shows that mysql is working. What I asked would show that it is working with php too.

---

### Post by Ginoxy on 2008-06-13
okay, now when i go to [http://localhost](http://localhost)
it does not give me "it works" line ! 
it gives me this 
[ATTACH]73888[/ATTACH]

---

### Post by acidsolution on 2008-06-13
Try to browse thru this 
[http://ubuntuforums.org/showthread.php?t=105747&page=2](http://ubuntuforums.org/showthread.php?t=105747&page=2)

---

### Post by Ginoxy on 2008-06-13
See the problem is i deleted wordpress by mistake and the only file that i have in /var/www is index.html , now when i want to install wordpress again it gives me that the folder is already exist ! i mixed up everything ;/

***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wordpress is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
***

---

### Post by acidsolution on 2008-06-13
try 
sudo dpkg-reconfigure wordpress 
 if this doesnot help than try to remove package and than install again 
sudo apt-get remove wordpress 

and 
sudo apt-get install wordpress

---

### Post by Ginoxy on 2008-06-13
ginoxy@ginoxy-desktop:/var/www$ sudo apt-get remove wordpress
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php5-mysql libphp-phpmailer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wordpress
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4649kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142812 files and directories currently installed.)
Removing wordpress ...
ginoxy@ginoxy-desktop:/var/www$ sudo apt-get install wordpress
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wordpress
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/874kB of archives.
After this operation, 4649kB of additional disk space will be used.
Selecting previously deselected package wordpress.
(Reading database ... 142277 files and directories currently installed.)
Unpacking wordpress (from .../wordpress_2.3.3-1ubuntu1_all.deb) ...
Setting up wordpress (2.3.3-1ubuntu1) ...


***

it is not in /var/www !!

---

### Post by acidsolution on 2008-06-13
i guess if its just php files missing from 
/var/www directory than you can download wordpress according to version installed in your computer and than work ..
you can give a try 
[http://wordpress.org/download/release-archive/](http://wordpress.org/download/release-archive/)

if suppose your version is 2.3.3 
than download .
[http://wordpress.org/wordpress-2.3.3.tar.gz](http://wordpress.org/wordpress-2.3.3.tar.gz)
extract and than place in /var/www/

---

### Post by Ginoxy on 2008-06-13
i moved it to /var/www it version 2.3.3
but still in the browser i can not access localhost !

---

### Post by acidsolution on 2008-06-13
whats the error now ?
is your apache running ???
try restarting apache
```
 sudo /etc/init.d/apache2 restart
``` 
also try other pages containing any small script if apache is running or not ?

---

### Post by ad_267 on 2008-06-13
Run this and then try to access it:

```
sudo /etc/init.d/apache2 restart
```

That will restart the apache web server.

---

### Post by Ginoxy on 2008-06-13
* Restarting web server apache2                                                Syntax error on line 1 of /etc/apache2/conf.d/fqdn:
Invalid command 'echo', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

---

### Post by ad_267 on 2008-06-13
I think you did this step wrong:

> echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn


That gives you a command to enter, you don't enter that into this file.

That file should look like this:
```
ServerName localhost
```

That error about "Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName" does not really matter anyways, so you could just delete this file.

But to fix this you can do:
```
gksudo "gedit /etc/apache2/conf.d/fqdn"
```

and make the file say only:
```
ServerName localhost
```

---

### Post by Ginoxy on 2008-06-13
seems like its working !!  :) but with this problem hehe 

any idea? 

[ATTACH]73902[/ATTACH]

---

### Post by Ginoxy on 2008-06-13
***
<?php
// ** MySQL settings ** //
define('DB_NAME', 'putyourdbnamehere');    // The name of the database
define('DB_USER', 'usernamehere');     // Your MySQL username
define('DB_PASSWORD', 'yourpasswordhere'); // ...and password
define('DB_HOST', 'localhost');    // 99% chance you won't need to change this value
define('DB_CHARSET', 'utf8');
define('DB_COLLATE', '');

// Change SECRET_KEY to a unique phrase.  You won't have to remember it later,
// so make it long and complicated.  You can visit [http://api.wordpress.org/secret-key/1.0/](http://api.wordpress.org/secret-key/1.0/)
// to get a secret key generated for you, or just make something up.
define('SECRET_KEY', 'put your unique phrase here'); // Change this to a unique phrase.

// You can have multiple installations in one database if you give each a unique prefix
$table_prefix  = 'wp_';   // Only numbers, letters, and underscores please!

// Change this to localize WordPress.  A corresponding MO file for the
// chosen language must be installed to wp-content/languages.
// For example, install de.mo to wp-content/languages and set WPLANG to 'de'
// to enable German language support.
define ('WPLANG', '');

/* That's all, stop editing! Happy blogging. */

define('ABSPATH', dirname(__FILE__).'/');
require_once(ABSPATH.'wp-settings.php');
?>
***

what should i put in my case ?

---

### Post by ad_267 on 2008-06-13
These are the three lines you need to change:

```
define('DB_NAME', 'putyourdbnamehere'); // The name of the database
define('DB_USER', 'usernamehere'); // Your MySQL username
define('DB_PASSWORD', 'yourpasswordhere'); // ...and password
```

Your username is probably just going to be "root" and password is whatever password you set.
I think you need to create a database for wordpress before it can install itself properly, although one may have already been created when you installed the wordpress package.

To see if there is already a database run the mysql client by entering "mysql -u yourusername -p" and enter your password and then:
```
SHOW DATABASES;
```

If there's one called wordpress or something then enter this where it says putyourdbnamehere. If there isn't anything that looks like wordpress then enter:
```
CREATE DATABASE wordpress;
```
and change putyourdbnamehere to wordpress

---

### Post by Ginoxy on 2008-06-13
root@ginoxy-desktop:/var/www/wordpress# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

this is what i got 

and by the way "SHOW DATABASES" does not work !

The program 'show' is currently not installed.  You can install it by typing:
apt-get install nmh
bash: show: command not found

---

### Post by ad_267 on 2008-06-13
You need -p on the end to say you're going to use a password.

Use:
```
mysql -u root -p
```

You type "SHOW DATABASES;" once you are logged into mysql. It doesn't work on the command line by itself.

---

### Post by Ginoxy on 2008-06-13
this is what i got 

***
ginoxy@ginoxy-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 21
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SHOW DATABASES
    -> 
***

---

### Post by ad_267 on 2008-06-13
You need the semi-colon on the end.

It's "SHOW DATABASES;"

Not "SHOW DATABASES"

If you still have that open you can just add the semi-colon on the next line and hit enter.

---

### Post by Ginoxy on 2008-06-13
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
+--------------------+
1 row in set (0.01 sec)

mysql>

---

### Post by ad_267 on 2008-06-13
Ok so there's nothing that looks like a wordpress database. So type:

```
CREATE DATABASE wordpress;
exit
```

And then you can change this line in your wp-config.php file:
define('DB_NAME', 'putyourdbnamehere'); // The name of the database
To:
define('DB_NAME', 'wordpress'); // The name of the database

---

### Post by Ginoxy on 2008-06-13
mysql> CREATE DATABASE wordpress;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'wordpress'

---

### Post by ad_267 on 2008-06-13
Did you log in as root to mysql? The user you log in as needs to be able to create a database.

---

### Post by Ginoxy on 2008-06-13
Its working NOW ! 

THANKS A LOT :guitar:

---

### Post by ad_267 on 2008-06-13
YAY! (You can click on the blue and yellow icon at the bottom right of my post to say thanks if you want.)

You will probably want to check out [http://wordpress.org/](http://wordpress.org/) for more information on wordpress and [http://themes.wordpress.net/](http://themes.wordpress.net/) for themes you can install to customize the look of your blog.

---

### Post by Ginoxy on 2008-06-13
Thanks again :) and you deserve not only one star .. lets say 100000 :) :KS

---

### Post by Ginoxy on 2008-06-14
Hello again, i think i forgot my password to log into wordpress admin is there any idea to recover it back ?

Thanks

---

### Post by ad_267 on 2008-06-14
> **Ginoxy said:**
> Hello again, i think i forgot my password to log into wordpress admin is there any idea to recover it back ?

Thanks

You can log in to mysql to change it:

```
mysql -u root -p
USE wordpress;
UPDATE wp_users SET user_pass = MD5('new-password') WHERE wp_users.user_login = "your_username";
```

---

### Post by Ginoxy on 2008-06-15
Again thanks a lot :) :KS

---


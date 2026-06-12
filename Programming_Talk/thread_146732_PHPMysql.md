---
title: "PHP/Mysql"
date: 2006-03-18
forum: Programming Talk
---

### Post by Darkness3477 on 2006-03-18
Hello everyone, yesterday my friend asked me  to help him with a website. 
What he asked was if I could show him how to make a website that allowed people to sign up, for him to validate or reject the people signing up, then those people who were validated could reach a members only area when signed in. 

Now, I though straight away that PHP and Mysql would be the easiest way to do this, but I could be wrong.  Now, not knowing much PHP I though I would find some source code, and perhaps tweak and edit it for his own needs, when I know a little bit more. 

Now, I've found a good website ([http://www.free2code.net/plugins/articles/read.php?id=99](http://www.free2code.net/plugins/articles/read.php?id=99)) that has a nice straight forward what-to-do on. Now, for those of you who are on the site, it's the first bit of code on the site, and those of you who are not on there, I'll post it:
```
<?php

//require the PEAR::DB classes.

require_once 'DB.php';


$db_engine = 'mysql';
$db_user = 'username';
$db_pass = 'password';
$db_host = 'localhost';
$db_name = 'database';

$datasource = $db_engine.'://'.
			  $db_user.':'.
			  $db_pass.'@'.
		 	  $db_host.'/'.
	  		  $db_name;


$db_object = DB::connect($datasource, TRUE);

/* assign database object in $db_object, 

if the connection fails $db_object will contain

the error message. */

// If $db_object contains an error:

// error and exit.

if(DB::isError($db_object)) {
	die($db_object->getMessage());
}

$db_object->setFetchMode(DB_FETCHMODE_ASSOC);

// we write this later on, ignore for now.

include('check_login.php');

?>
```

The site then says "There are various things you will have to customize     
    * $db_engine - Your database engine, a list of possible values is below.
    * $db_user - Your username to access the database.
    * $db_pass - Your password.
    * $db_host - The host of the database server.
    * $db_name - The name of the database to connect to."

Well, I know I have apache and PHP on my computer, and I'm almost positive I did a full lamp and got MySQL as well, but I don't ever rememer having to set up a username and password for the database. ANd the host of the databse server, well I'm doing it on my computer to test it out first, so what do I put? And I'm not sure what the databse name is, or which one I need to connect too. So, A little bit of help would be excellent and much appreciated.

---

### Post by dermotti on 2006-03-18
install phpymyadmin with synaptic.

Its a gui for mysql administration. It will also let you create users and set passwords.

The host usually is just "localhost".
You need to create a database
You need to create a user with a password and give them access to the database.

phpmyadmin will help you do all that.

Why are you tryign to write your own script anyways? You can get whole website management programs that are free and install in like 2 minutes.

Checkout out my site, its running php,mysql.

---

### Post by Darkness3477 on 2006-03-18
Programs that let you do all of this, and still have a normal site, however you want it designed? If so, where would I look for such a beutiful thing?

---

### Post by Darkness3477 on 2006-03-18
ONe other thing, I was doing it in scripts because I'm not sure about what he has on the server (HE has gotten some free space of a friend who runs a fairly large website), so I figured you wouldn't be able to install things like PHPmyadmin.

---

### Post by Darkness3477 on 2006-03-18
I just downloaded the MySQL Administrator, when I run it it asks for the server host name, so I put down localhost, I use the defualt port (3306) and then I put the username and password in, and then click connect.

As soon as I have done that, I get this error
Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.
I then ping it, and it seems to be working. So, what the hell is going wrong, and what am I supposed to do to access it?

---

### Post by Darkness3477 on 2006-03-18
Wait... that was MySQL adminstrator. I don't think they are the same things... I've downloaded  phpmyadmin but I cannot seem to find out where it is...

---

### Post by DoktorSeven on 2006-03-19
```

(Install MySQL server/client)
sudo apt-get install mysql-server mysql-client

(make sure MySQL is running)
sudo /etc/init.d/mysql start

(Change password for MySQL root user)
sudo mysqladmin password "whateveryouwant"

(log into MySQL as root, it will ask for your password, give it what you set it as above)
mysql -u root -p

(create a database and user for normal use)
create database mydatabase;

grant all privileges on mydatabase.* to myuser@localhost identified by 'mypassword';

(exit mysql)
quit

```
So in this example username is **myuser**, password is **mypassword**, server (host) is **localhost** (since it's being installed on the local machine, this won't change), and database is **mydatabase**.

---

### Post by Darkness3477 on 2006-03-19
Thanks. Is there any chance that you would know where phpmyadmin would be located on my computer, as I installed it via synaptic and now can't find it.

---

### Post by DoktorSeven on 2006-03-19
PHPMyAdmin is web-based, so it's usually installed off of your web home directory -- [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) is a likely candidate.

---

### Post by Darkness3477 on 2006-03-19
Thanks, I found that not long ago... But still, this just isn't working for me...

---

### Post by LordHunter317 on 2006-03-19
[QUOTE=Darkness3477]Hello everyone, yesterday my friend asked me  to help him with a website. 
What he asked was if I could show him how to make a website that allowed people to sign up, for him to validate or reject the people signing up, then those people who were validated could reach a members only area when signed in. 

Now, I though straight away that PHP and Mysql would be the easiest way to do this, but I could be wrong.[/quote]You were.  HTTP Digest auth would have been the eaisest way.

---

### Post by Darkness3477 on 2006-03-20
Ok, I've just got it working, well, it coming up with no error messages. But when I go to register it says "DB Error: no such table" So, how do I created the table?

---

### Post by David Marrs on 2006-03-20
Read the [mysql tutorial](http://dev.mysql.com/doc/refman/5.0/en/tutorial.html). It will give you a good start.

---

### Post by jeffmetal on 2006-03-20
If you read the tutorial you have to run the table.php page first so its creates the tables for you then you use can play around with it.

the only problem is that i get the following error when it try to use table.php
```

Warning: main(DB.php) [function.main]: failed to open stream: No such file or directory in /home/jeffrey/public_html/site/db_connect.php on line 5

Fatal error: main() [function.require]: Failed opening required 'DB.php' (include_path='.:/usr/share/php:/usr/share/pear') in /home/jeffrey/public_html/site/db_connect.php on line 5

```

I installed php5-pear and it still dont like it. My guess is that pear is actually located in /usr/share/php/pear so that include_path line is wrong. just dont have a clue as to where i can change it.

---

### Post by Darkness3477 on 2006-03-21
Thanks, that helped alot. Everything now works just fine!

---

### Post by shadwstalkr on 2006-03-21
Unless this is an academic excercise, you're probably just wasting your time.  You should install a CMS and spend your time customizing that.  You'll get more flexibility, better security, and better performance.  Off the top of my head, Wordpress, Drupal, and Expression Engine would give you a good cross-section of features to explore before you choose one, but searching Google for "free cms" will give you as many options as you can handle.

---

### Post by Darkness3477 on 2006-03-22
IN a sence, it is an academic excercise. Both myself and the friend I are doing this for the learning experience, as we both like to know as much as we can about everything, and also, this was the first thing that popped into my mind, and I have spent too much time working this out to just drop it.

Also, I think (as I learn more about PHP) that I'll be able to add more features and customization for his website using PHP, so I might as well use it for everything.

---

### Post by Darkness3477 on 2006-03-22
IN a sence, it is an academic excercise. Both myself and the friend I are doing this for the learning experience, as we both like to know as much as we can about everything, and also, this was the first thing that popped into my mind, and I have spent too much time working this out to just drop it.

Also, I think (as I learn more about PHP) that I'll be able to add more features and customization for his website using PHP, so I might as well use it for everything.

---


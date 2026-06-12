---
title: "Running PHP scripts with Cron jobs"
date: 2010-03-20
forum: Programming Talk
---

### Post by gmc1200 on 2010-03-20
I'm tryin to run a PHP script I have on my XAMPP server every 30 minutes with cron, but it just doesn't seem to work. It seems like when you have things set to run with cron, it's essentially like executing commands in the terminal.

I have the following in my crontab:

```
* * * * * php /opt/lampp/htdocs/app/index.php

```

When I run ```
php /opt/lampp/htdocs/app/index.php

``` in the terminal, I get this output:

```
Fatal error: Call to undefined function mysql_connect() in /opt/lampp/htdocs/app/index.php on line 2

```

I was searching around, people were mentioning uncommenting extention="mysql.so"; in my php.ini file, but I didn't see that in there.

Does anyone have a clue to what's going wrong?

Thanks

---

### Post by Hellkeepa on 2010-03-20
HELLo!

Make sure you've installed the php-mysql libraries, and if you've done that you can just add that missing line to the "php.ini" file. Just look for it in the package manager, should be pretty apparent what you need. ;-)

Happy codin'!

---

### Post by gmc1200 on 2010-03-20
> **Hellkeepa said:**
> HELLo!

Make sure you've installed the php-mysql libraries, and if you've done that you can just add that missing line to the "php.ini" file. Just look for it in the package manager, should be pretty apparent what you need. ;-)

Happy codin'!

Turns out I didn't have the php-mysql installed...but I installed it and it's still not working.:(

```
Warning: mysql_connect(): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /opt/lampp/htdocs/app/index.php on line 2
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Also, does it matter where I add the line in the php.ini file?

---

### Post by Hellkeepa on 2010-03-20
HELLo!

That's a completely different errror you're getting there, one that tells you that the PHP-MySQL library is indeed loaded and working. The package manager adds that line into the "php.ini" itself, when installing the libraries.
However, you don't seem to have a MySQL server running, or at least the socket file is not where PHP expects it to be. Do a "find / -name mysql.sock" to find out where it is. First, however, make sure you've got MySQL installed and running.

Happy codin'!

---

### Post by soltanis on 2010-03-20
> **gmc1200 said:**
> It seems like when you have things set to run with cron, it's essentially like executing commands in the terminal.

It's actually exactly like executing commands in a terminal; the resulting output is mailed to you, but otherwise cronjobs just periodically run shell commands.

By the way, the crontab entry you listed will run that command every minute, not every 30 minutes. Every 30 minutes is instead:

```

*/30 * * * * php ...
# or
0,30 * * * * php ...

```

---

### Post by gmc1200 on 2010-03-22
I'm pretty sure I already have MySQL installed; I'm using [XAMPP]("http://www.apachefriends.org/en/xampp.html").

I ran the find / -name mysql.sock

```
find: `/opt/lampp/var/mysql/mysql': Permission denied
find: `/opt/lampp/var/mysql/cdcol': Permission denied
find: `/opt/lampp/var/mysql/phpmyadmin': Permission denied
find: `/opt/lampp/var/mysql/df': Permission denied
find: `/opt/lampp/var/mysql/test': Permission denied
/opt/lampp/var/mysql/mysql.sock
find: `/opt/lampp/var/mysql/dontforget': Permission denied
find: `/opt/lampp/tmp/eaccelerator': Permission denied
```

@soltanis, yep, I know that it's running every minute, just had it that way for testing purposes!:P

---

### Post by Hellkeepa on 2010-03-22
HELLo!

That's your problem right there: You haven't used the package manager to install the server software, but you used it to install PHP5-CLI. That means that PHP5-CLI expects the "mysql.sock" file to be present in a certain location, where it would be if you'd used the package manager to install MySQL. Since you didn't the file is stored in a completely different location, as evidenced above, and PHP won't find it.

What you need to do is to create a symlink where PHP looks, which points to the correct location. You could could configure PHP to look in the right place, but the symlink approach is by far the easiest one; Saves you from having to reconfigure every single MySQL-using application that you install via the packaga manager.

Happy codin'!

---

### Post by gmc1200 on 2010-03-22
> **Hellkeepa said:**
> HELLo!

That's your problem right there: You haven't used the package manager to install the server software, but you used it to install PHP5-CLI. That means that PHP5-CLI expects the "mysql.sock" file to be present in a certain location, where it would be if you'd used the package manager to install MySQL. Since you didn't the file is stored in a completely different location, as evidenced above, and PHP won't find it.

What you need to do is to create a symlink where PHP looks, which points to the correct location. You could could configure PHP to look in the right place, but the symlink approach is by far the easiest one; Saves you from having to reconfigure every single MySQL-using application that you install via the packaga manager.

Happy codin'!

Thanks Hellkeepa...once more thing, would you be able to point me to a tutorial on symlink? Calling me a noob would be an understatement.

---

### Post by Hellkeepa on 2010-03-22
HELLo!

```
man ln
```
Or even googling for "symlink howto" should give you all the information you need.

Happy readin'!

---

### Post by gmc1200 on 2010-03-30
The symlink wasn't working for me and I think I did something that screwed up my XAMPP set up, so I just decided to start from scratch and install the LAMP components manually using this tutorial I found: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

I got everything set back up again and everything works fine just opening it from the browser, but I'm still having issues running from the command line. With LAMP installed, I still wasn't able to execute my script from the terminal, so I installed php5-cli.

So I do:

```
php -f /path/to/script.php
```

and I get:

```
PHP Deprecated: Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown line 0
Could not open input file: /path/to/script.php
```

So it looks like I opened up a set of new problems...

Any suggestions?

---

### Post by Reiger on 2010-03-30
Okay this will sound stupid: but does the file /path/to/script.php actually exist? 'Cause that is what you attempt to execute with php -f.

---

### Post by gmc1200 on 2010-03-30
> **Reiger said:**
> Okay this will sound stupid: but does the file /path/to/script.php actually exist? 'Cause that is what you attempt to execute with php -f.

No, that didn't sound stupid. I am stupid. Turns out that I didn't copy over the script to the folder, so it wasn't there.

So I put the script where it needed to be and now it's working! Thank you!!!!

Will the "depracated" message cause any issues? Is there something else that I should be using instead?

Thanks again!

---

### Post by Hellkeepa on 2010-03-31
HELLo!

The deprecated message can safely be ignored, as it is a notice only. However, should it annoy you, it's quite simple to just replace the # comments with //. ;-)

Happy codin'!

---


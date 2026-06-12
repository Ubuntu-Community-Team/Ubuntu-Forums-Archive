---
title: "LAMPP - MYSQL Terminal Not Working"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by khan3 on 2014-09-10
Hi,

I've installed LAMPP from the package i ran.

When i try to login to mysql in the terminal (mysql -u root -p) it says this package is not installed.

Am i missing something? I thought lampp installs mysql.

---

### Post by yancek on 2014-09-10
In a terminal, type whereis mysql and see what output you get.  What method did you use to install LAMP?

---

### Post by khan3 on 2014-09-12
This is how i installed xampp.

[http://ubuntuportal.com/2013/12/how-to-install-xampp-1-8-3-for-linux-in-ubuntu-desktop.html](http://ubuntuportal.com/2013/12/how-to-install-xampp-1-8-3-for-linux-in-ubuntu-desktop.html)

i used the latest version of xampp.

where is mysql returns this

mysql: /opt/lampp/bin/mysql /opt/lampp/bin/mysql.server

Seems like its installed as i have access to phpmyadmin and can create dbs from there. i just cnt login via the terminal

---

### Post by Lars Noodén on 2014-09-12
> **khan3 said:**
> Hi,

I've installed LAMPP from the package i ran.

When i try to login to mysql in the terminal (mysql -u root -p) it says this package is not installed.

Am i missing something? I thought lampp installs mysql.

You're missing the easy way. ;)  LAMPP/XAMPP is doable if you really want that, but it is a very difficult way to get Apache and MySQL.  It is also a lot more work and attention to keep maintained and get security updates.  Further, it puts things in weird places.   It is more of a crutch for people still on Windows.  

If you remove the old XAMPP stuff you can find Apache, MySQL and PHP in the Software Center or with Synaptic.  Perl and Python are already included and do not need to be installed special.  Or you can do the following two lines in a terminal.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Note the caret.  

By using the versions in the repositories (getting them via the Software Center, Synaptic or apt-get) you can get automatic updates especially security updates, automated starting, stopping, and monitoring of daemons and most helpfully, the programs and data will be in locations people here expect them to be.  So it will be much easier to get help here or on other forums where Ubuntu is discussed.

---

### Post by khan3 on 2014-09-12
Yeah i have installed other stuff using the terminal, dunno why i did it this way with lampp, prob because i just followed the first guide on a search.

So i can just simply uninstall my current lampp and do it your way, i guess i have to backup my dbs aswell.

---

### Post by khan3 on 2014-09-13
I tried to install using ur method but during the process i got this error.

                                                                         [fail]
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems
invoke-rc.d: initscript apache2, action "restart" failed.
apache2_invoke: Enable module php5
 *  Restarting web server  apache2                                                AH00558: apache2:  Could not reliably determine the server's fully qualified domain name,  using 127.0.1.1. Set the 'ServerName' directive globally to suppress  this message
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems
invoke-rc.d: initscript apache2, action "restart" failed.
Setting up php5-json (1.3.2-2build1) ...
php5_invoke: Enable module json for cli SAPI
php5_invoke: Enable module json for apache2 SAPI
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
W: Operation was interrupted before it could finish

---

### Post by khan3 on 2014-09-13
When it is installed where does it put the lampp/htdocs folder? same place as before opt/lamp/htdocs?

---

### Post by khan3 on 2014-09-13
Even with the error, i restarted and tried to install again. localhost gives me the -             Apache2 Ubuntu Default Page         and mysql allows me to login. I will have to install phpmyadmin seperatly? still the /opt/ folder contains no lamp folder and thus no htdocs.

---

### Post by Lars Noodén on 2014-09-13
> **khan3 said:**
> (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down

Do you have the old XAMPP still installed and running?  If there is already an httpd listening on port 80 then a second one cannot use that port.   It has to be cleared first.

---

### Post by khan3 on 2014-09-13
So i assume for my websites i now use. var/www/html > this is where the index page is for apache it works.

If i want to have multiple websites do i just put the folders in var/www. e.g.

var/www/website1/index.php
var/www/website2/index.php

and if i want to access them i use

localhost/website1/index.php
localhost/website2/index.php

is this right?

---

### Post by khan3 on 2014-09-13
> **Lars Noodén said:**
> Do you have the old XAMPP still installed and running?  If there is already an httpd listening on port 80 then a second one cannot use that port.   It has to be cleared first.

ye i think that was the issue so i stoped/restarted linux and just did an install and it finished of the rest of the stuff.

---

### Post by Lars Noodén on 2014-09-13
> **khan3 said:**
> So i assume for my websites i now use. var/www/html > this is where the index page is for apache it works.



The default [virtual host](https://httpd.apache.org/docs/2.4/vhosts/) sets its [DocumentRoot](https://httpd.apache.org/docs/2.4/mod/core.html#documentroot) to /var/www/html.  So, yes, for the first site, you put your first site in /var/www/html

> **khan3 said:**
> 
If i want to have multiple websites do i just put the folders in var/www. e.g.

var/www/website1/index.php
var/www/website2/index.php


Yes. You'll also need to set up one additional configuration file for each new virtual host.  These go in /etc/apache2/sites-available/ and can be based on modified versions of the default example already in that directory.  Then once you have the files ready, enable the new sites with 'sudo a2ensite'

> **khan3 said:**
> 
and if i want to access them i use

localhost/website1/index.php
localhost/website2/index.php

is this right?

Close.  You probably want to set up name-based virtual hosts. 

[http://website1/index.html](http://website1/index.html)
[http://website2/index.html](http://website2/index.html)

etc.

If you're accessing as localhost, you can add fake names to /etc/hosts on the line with localhost.  Then you can access each site separately by domain name.  Note that this method only works if your browser is on the same machine as the web server.  If you want name-based virtual hosts from another machine you will either need different DNS trickery or real domain names.

---

### Post by khan3 on 2014-09-13
Nice that's pretty cool, do you know of a good tutorial on how to setup what u just said with the config file and multiple sites, using the fake names as the server is on the same machine.

---

### Post by Lars Noodén on 2014-09-13
Here's one for 14.04 that looks ok:

[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

The official documentation from Apache is not that helpful until you've done it at least once before.  Then it starts to make sense.  But it's worth looking at both before you start and then again after you are done.  

About /etc/hosts, you can add the names on the same line as "localhost".  Just separate  the names with a space and add them at the end of the line.  Try pinging them to see that they work.  Or you can add them with unique IPv4 numbers, one per line.  Any numbers in the 127.0.0.0/8 range are avaiable.  (And be sure to make a backup copy of /etc/hosts or any other important file before changing it.  It's better to have a backup but not need it than the other way around.)

---


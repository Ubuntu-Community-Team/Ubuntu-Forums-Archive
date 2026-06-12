---
title: "Problem starting mysql"
date: 2015-02-25
forum: New to Ubuntu
---

### Post by 0N3 on 2015-02-25
I cant seem to start mysql from xampp control panel

Here is the output from a terminal

```
david@David-PC:~$ sudo /opt/lampp/lampp start[sudo] password for david: 
Starting XAMPP for Linux 5.6.3-0...
XAMPP: Starting Apache...already running.
XAMPP: Starting MySQL...ok.
XAMPP: Starting ProFTPD...already running.
```

When I try connect to wordpress I get an error saying error connecting to database.

Here is the GUI of xampp control panel

[ATTACH=CONFIG]260212[/ATTACH]

When I try execute nothing happens. I checked my wp-config file and everything is as should be. It was working fine yesterday! Any help appreciated.

---

### Post by Lars Noodén on 2015-02-25
The main problem would be all that lampp stuff in /opt/  ;)  It does not take advantage of either the package manager or the process management tools.  The latter is biting you right now the former will bite you when a security patch is needed.  LAMPP installs things in non-standard places and in some cases even adds redunant, conflicting pieces.  It might be ok on a Windows system, where installation is hard, but it is one of the most difficult ways possile to deal with MySQL or Apache on Ubuntu.  

My recommendation would be to step back and remove LAMPP and install using the Linux method:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Mind the caret (^) it is part of the meta-package name.  

That will get you Apache2, MySQL, and PHP.  Working versions of Perl and Python are already installed on your system.  Using that method then allows you to stay up to date automatically, including security updates, rather than having to fight manually with the system.  It also takes advantage of the process management tools that allow you to start, stop and monitor processes automatically.  And it puts programs and data in standard, expected locations so that it is easy for people here to help when there is a problem.

---

### Post by 0N3 on 2015-02-25
Thanks for the quick reply Lars I will try that now see how I get on! Will be back if problems.

---

### Post by Lars Noodén on 2015-02-25
Sure thing.  

It will also let you take advantage of the many official help documents like the Server Guide

[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

Or just ask here, there are many that use Apache2 and MySQL.

---

### Post by 0N3 on 2015-02-25
Got that working now thank you! Really appreciated! Can I make or is there a .desktop file for starting Apache and MYSQL?

---

### Post by Lars Noodén on 2015-02-25
Both should start up automatically when the system starts.  If you want to stop them manually you can use *service* to manage the process.

```

sudo service apache2 stop
sudo service apache2 start
sudo service apache2 restart

sudo service mysql stop
sudo service mysql start
sudo service mysql restart

```

If you don't want them to start at all when your machine starts, then that can be set so they must be started manually.

---

### Post by 0N3 on 2015-02-25
The websites I am testing are working fine as expected! Wordpress just same error connecting to database. I am not sure if I was supposed to 

```
sudo chmod 777 -R /var/www/


```

If not how do I remove permissions? I could setup a new database as these are only for testing. I tried localhost/phpmyadmin but got error: [COLOR=#000000][FONT=Times New Roman]The requested URL /phpmyadmin/ was not found on this server.

How can I setup a new database?[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-02-25
> **0N3 said:**
> The websites I am testing are working fine as expected! Wordpress just same error connecting to database. I am not sure if I was supposed to 

```
sudo chmod 777 -R /var/www/


```

If not how do I remove permissions?

The defaults for the directory were 755 and 644 for the files in the directory.  They can be restored with the help of [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html)

```

sudo find /var/www/ -type d -exec chmod u=rwx,g=rx,o=rx "{}" \;
sudo find /var/www/ -type f -exec chmod u=rw,g=r,o=r "{}" \;

```

About setting up the initial database, which guide are you following?  And are you on Ubuntu 14.04 LTS?

---

### Post by Holger_Gehrke on 2015-02-25
> **0N3 said:**
> The websites I am testing are working fine as expected! Wordpress just same error connecting to database. I am not sure if I was supposed to 

```
sudo chmod 777 -R /var/www/

```

Please don't. Never make anything world-writable, especially not web-site directories. It's better to figure out which parts the server actually needs to write to (it's either documented or easy to find out by trial and error) and 'chown' them to the user the server runs as (usually the user 'www-data')

> **0N3 said:**
> 
If not how do I remove permissions? I could setup a new database as these are only for testing. I tried localhost/phpmyadmin but got error: [COLOR=#000000][FONT=Times New Roman]The requested URL /phpmyadmin/ was not found on this server.

How can I setup a new database?[/FONT][/COLOR]

I don't think phpmyadmin is installed as part of the lamp-stack. You can check whether it's installed by trying 'apt-cache policy phpmyadmin' in a shell. If it's not installed, a simple 'sudo apt-get install phpmyadmin' will download and install it.

---

### Post by 0N3 on 2015-02-25
I am following this tutorial 
```
https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04
```

Sorry I am a student doing degree in Information Technology I DON'T want to use windows for anything unless I have to I am a bit of an open source junkie :) (with the exception of photoshop) We're thought photoshop so I don't really have a choice! LibreOffice, BlueGriffon and Eclipse do me fine for now and have done for past two years!

---

### Post by 0N3 on 2015-02-25
ThanksHolger I will try that as I am more familiar with that way.[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578")

---

### Post by 0N3 on 2015-02-25
Well that ended up being easy I really complicated it! Thanks for both of your help Lars & Holger much appreciated! Sorted!

---


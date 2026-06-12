---
title: "Command line php"
date: 2007-01-23
forum: Programming Talk
---

### Post by Ryanmt on 2007-01-23
Im trying to write a php program that runs as server, Ive installed xammp but i still get php: command not found.

What do i need to do to run/install command line php applications?

Thanks
Ryan

---

### Post by tocleora on 2007-01-23
If you're running php 5 run this:

```
sudo apt-get install php5-cli
```

php 4:

```
sudo apt-get install php4-cli
```

That should take care of it.  :guitar:

---

### Post by Dygear on 2007-01-24
On the windows side of things, you just have to add php.exe to the path system variable.

---

### Post by Dygear on 2007-01-24
Request this post be deleted!

---

### Post by Ryanmt on 2007-01-25
That did the trick Thanks. However im having problems with sql.

Im making a server interface to phpBB.

I everything setup and working ok with xammp for the http:// side of the forum, the mysql database is up and running.

I now need to access the same database from the command line. Ive tried including the default connect file from phpbb and it says ..

Fatal error: Call to undefined function mysql_connect() in /opt/lampp/htdocs/phpBB2/db/mysql4.php on line 48


i read that it could be a php.ini setting however im not sure what i need to do!

---

### Post by maddog39 on 2007-01-25
The problem is that XAMPP is it's own self contained package and it doesnt install anything on the system (in the system directories) per se.

Therefore, you also have to install mysql.
```

sudo apt-get install mysql5-client && sudo apt-get install mysql5-server

```
Then I think you need to enable it by uncommenting the module in the php.ini file which is located here:
> /etc/php5/cli/php.ini

---

### Post by Ryanmt on 2007-01-25
will i still be accessing hte same database i have running that way or will that be a totally seperate version of mysql running?

if its seperate will i need to install phpmyadmin into it, how will i go about setting up local host then :s Thanks

---

### Post by Ryanmt on 2007-01-25
ryanmt@penguin:/etc/php5/cli$ sudo apt-get install mysql5-client && sudo apt-get install mysql5-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql5-client


:(

---

### Post by Ryanmt on 2007-01-25
i just tried to install it from the synaptic and it failed on setting the server up (bring it back online to be exact).

Im lost here, can anybody point me in the direction of a good guide. How do i go about getting of hte stuff ive already setup to avoid confusion.

---

### Post by tocleora on 2007-01-25
I've tried xampp before and had bad luck with it due to it's configuration, so my suggestion is to uninstall it and install everything directly.  In Synaptic you can install apache(2), php(5) and mysql(5).  You'll want to make sure you include the mysql module for php (php5-mysql).  I think phpmyadmin is in synaptic too but I think webmin (if you use it) has to be installed from the .deb on their web site.  Then you should be able to use both from the same database.  Respond back here if you have problems.

---

### Post by Ryanmt on 2007-01-25
I got that working all ok now so it seems. I wish i had backed up my old msql database though *muppet*

Thanks :)

---

### Post by maddog39 on 2007-01-25
Okay, well a while back I made a shell script to install a complete server installation from the ubuntu repositories for a friend, and it works for sure (in edgy). So I have attached it. Just run:
```
cd Desktop;chmod +x lamp.sh;./lamp.sh
```Should work to run the script. It will install PHP5, MySQL 5, PHP5-GD, PHP5-CLI, and phpMyAdmin

---

### Post by tocleora on 2007-01-25
That script I'm sure will be very handy for others on this site as well.  Very cool!

---

### Post by jelkimantis on 2007-01-25
> **maddog39 said:**
> Okay, well a while back I made a shell script to install a complete server installation from the ubuntu repositories for a friend, and it works for sure (in edgy). So I have attached it. Just run:
```
cd Desktop;chmod +x lamp.sh;./lamp.sh
```Should work to run the script. It will install PHP5, MySQL 5, PHP5-GD, PHP5-CLI, and phpMyAdmin

you could always dl  a LAMP Virtual machine from [www.rpath.com](www.rpath.com), then you can develop with it and then trash it if you mess up.

jsl

---


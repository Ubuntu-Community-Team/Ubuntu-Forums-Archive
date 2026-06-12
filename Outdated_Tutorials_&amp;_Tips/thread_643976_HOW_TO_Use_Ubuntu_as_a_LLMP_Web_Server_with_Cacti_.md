---
title: "HOW TO: Use Ubuntu as a LLMP Web Server with Cacti (part 4/4)"
date: 2007-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by uberamd on 2007-12-18
This guide will show you (yes show, it has pictures) how to configure a standard Ubuntu 7.10 install to act as a LLMP (Linux Lighttpd MySQL PHP) server. I will also show you how to install the Cacti statistics and server status software package.

**Right away, open up a terminal *(Applications* > *Accessories* > *Terminal)* as everything we do will be in the terminal**

First, make sure you have set the password to your root account. If you have not, do:
```
$ sudo passwd root
```
You will be asked to type in a root password, so come up with a password for the 'root' account and press enter. Confirm the password, press enter again, and your set.

Now that your root password is set, do:
```
$ su -
Password
```
And you should be at a prompt that looks something like this (note the # sign):
[img]http://images.phpsn.net/images/llmp1.png[/img]

Now we will want to update our apt-get packages. Apt-get is the Ubuntu/Debian Package Delivery System for installing new packages from remote servers onto your system. Run:
```
# apt-get update
```
And you should see output similar to below:
[img]http://images.phpsn.net/images/llmp2.png[/img]

**Installing the Lighttpd Web Server**

Your output may be more elaborate if you have never run apt-get update before but it will be relatively the same. Now that we are all up to date, we will install the Lighttpd web server. Follow the steps (what I typed is displayed after the # sign, remember that):
[img]http://images.phpsn.net/images/llmp3.png[/img]

Press Y at the prompt below:
[img]http://images.phpsn.net/images/llmp4.png[/img]

Once it is done installing you should see something similar to (note the Starting web server lighttpd [ OK ]):
[img]http://images.phpsn.net/images/llmp5.png[/img]

At this point the web server is installed, and working. Going to a web browser and going to the URL: [http://localhost/](http://localhost/) SHOULD give you this page:
[img]http://images.phpsn.net/images/llmp6.png[/img]

If you do not see a page like the one above, and get something like this, you encountered a problem:
[img]http://images.phpsn.net/images/llmp7.png[/img]

Now that we have Lighttpd working, here are a few commands to control it:
[img]http://images.phpsn.net/images/llmp8.png[/img]

The first command: **killall lighttpd** will kill the server (stop lighttpd from running). Thus, when you go to localhost you get the server problem page. To start the server up again you use **lighttpd -f /etc/lighttpd/lighttpd.conf** which forces the server to start using the config file found in /etc/lighttpd. It really is that easy.

---

### Post by uberamd on 2007-12-18
**Installing PHP**

PHP is what almost every server has running. PHP is an engine that processes PHP code into browser-readable content. Because PHP is so powerful, we will be installing it onto our server. Lets get started. Perhaps you can guess what the command is, if not:
[img]http://images.phpsn.net/images/llmp9.png[/img]

Then:
[img]http://images.phpsn.net/images/llmp10.png[/img]

And:
[img]http://images.phpsn.net/images/llmp11.png[/img]

And:
[img]http://images.phpsn.net/images/llmp12.png[/img]

Now we have PHP installed, with CGI mode, MySQL, and CLI supported. Now we need to enable fastcgi mode in lighttpd:
[img]http://images.phpsn.net/images/llmp13.png[/img]

And restart lighttpd (like the direction in the terminal says) using **# /etc/init.d/lighttpd force-reload** and we should see:
[img]http://images.phpsn.net/images/llmp14.png[/img]

(Notice the 2 [ OK ]'s, thats good). Now we can test and make sure PHP is working. Lets move into the www folder where our webpages will be stored:
```
# cd /var/www
```
And type: **# pico test.php** and you should get a blank editor window. Fill it in like shown below:
[img]http://images.phpsn.net/images/llmp15.png[/img]

Then press **Control O** to save it and **Control X** to exit. Now go to your web browser and go to the URL **[http://localhost/test.php](http://localhost/test.php)** and you should see something similar to:
[img]http://images.phpsn.net/images/llmp16.png[/img]

If you see something similar to the image above, you are doing great so far! The wording will be different but it should in general look similar. Congrats, you now have PHP and Lighttpd running together. The final step is getting MySQL going.

---

### Post by uberamd on 2007-12-18
**Installing MySQL**

Much like how we installed PHP and Lighttpd, do: 
[img]http://images.phpsn.net/images/llmp17.png[/img]

It is going to download ~33MB of data so be patient as apt-get works its magic. You are going to want to setup a root password as well. After it is complete, you should see something similar to:
[img]http://images.phpsn.net/images/llmp18.png[/img]

Note that if you were never prompted to set your mysql password you can use the command (if you have set the password, skip this set): 
```
# sudo mysqladmin -u root password "YourPasswordGoesHere"
```
To check your mysql server, type (**# mysql -u root -p**):
[img]http://images.phpsn.net/images/llmp19.png[/img]

If you get something like the image above, it works. **\q** will exit mysql. Now we will make a new database called trial:
[img]http://images.phpsn.net/images/llmp20.png[/img]

To make sure the database was created we can try to delete it:
[img]http://images.phpsn.net/images/llmp21.png[/img]

So we are able to create and delete databases! Yay. Now lets install phpmyadmin so we can easily manage our databases. Type:
```
# apt-get install phpmyadmin
```
You will get a screen like below, just go to OK, do not check any boxes:
[img]http://images.phpsn.net/images/llmp22.png[/img]

Once it is done installing, we will need to move it to /var/www:
[img]http://images.phpsn.net/images/llmp23.png[/img]

Now restart lighttpd (the commands are above), and in your browser try to go to **[http://localhost/phpmyadmin](http://localhost/phpmyadmin)** The output should look similar to the one below:
[img]http://images.phpsn.net/images/llmp24.png[/img]

Wow, we have accomplished a lot so far. MySQL, PHP, and Lighttpd all working with phpmyadmin to manage databases. Whats left? Well, nothing really, However if you want to install cacti (server status and statistics) follow the steps below.

---

### Post by uberamd on 2007-12-18
**Installing Cacti**
[i]
Cacti is a complete network graphing solution designed to harness the power of RRDTool's data storage and graphing functionality. Cacti provides a fast poller, advanced graph templating, multiple data acquisition methods, and user management features out of the box. All of this is wrapped in an intuitive, easy to use interface that makes sense for LAN-sized installations up to complex networks with hundreds of devices[/i].

Start with the following command:
[img]http://images.phpsn.net/images/llmp25.png[/img]

When you reach the screen below, select 'None':
[img]http://images.phpsn.net/images/llmp26.png[/img]

At the screen below select 'Yes':
[img]http://images.phpsn.net/images/llmp27.png[/img]

At the screen below type in your MySQL root password (which you set above) and select 'Ok':
[img]http://images.phpsn.net/images/llmp28.png[/img]

At the screen below, enter the same password as your MySQL root password and select 'Ok':
[img]http://images.phpsn.net/images/llmp29.png[/img]

Then confirm the password:
[img]http://images.phpsn.net/images/llmp30.png[/img]

Now we need to link the cacti folder to our web directory folder:
[img]http://images.phpsn.net/images/llmp31.png[/img]

We can now go to [http://localhost/cacti/site/](http://localhost/cacti/site/) in our web browser and you should see a screen like below:
[img]http://images.phpsn.net/images/llmp32.png[/img]

Follow the promps and you will get to the login screen. The username and password are both **admin**

Once you are logged in, you can manage the graphs. I will not go in depth about that as you can read the manual.

**We are now done! Congrats**, you have a WORKING Linux server running Lighttpd, MySQL 5, PHP 5 with phpmyadmin and Cacti installed! It really is that simple, all of that can be completed in under 30 minutes!

If you enjoy this tutorial, please say thank you and do not rip it off, I spent quite a bit of time going through the steps, checking my work, and making sure it was easy to follow by taking many screenshots and would like to receive a little credit. Enjoy the tutorial and the new server!

Thank me if you enjoy the guide.

---

### Post by detyabozhye on 2008-01-24
awsum guide, I needed the phpmyadmin part, but all I did was make a symbolic link to it in /var/www/ instead of moving it. It's better that way in case of updates:

```
$ sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

### Post by cybernet on 2008-03-18
actualy is 37.2MB for mysql-server and client :D

like you said apt-get is magic :lolflag:

---

### Post by plmday on 2008-04-02
Excellent! Thanks! :)
Don't use ```
apt-get install mysql
``` to install the mysql server, it does not match anything, use ```
apt-get install mysql-server
``` instead. ;-)

---

### Post by boob11 on 2009-01-20
thnx

---

### Post by harry71194 on 2009-08-25
Thanks very much, sir! :)

---


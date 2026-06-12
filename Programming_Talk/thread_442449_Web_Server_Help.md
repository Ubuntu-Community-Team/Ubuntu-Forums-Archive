---
title: "Web Server Help"
date: 2007-05-13
forum: Programming Talk
---

### Post by adam93250 on 2007-05-13
Ok, i want to setup a Web Server.
I need to install, on this computer:
A Web Server
PHP 5
MySQL 5

I only know how to setup MySQL.
I would like to know a good webserver system, and how to install it.
I was thinking of using Apache, but i cant install the C Compiler.

---

### Post by kbf on 2007-05-13
You might want to use this 

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)
:)

---

### Post by ep2011 on 2007-05-13
If its a computer dedicated to the server, your better off just running Ubuntu server edition (No gui, only command line), configuring the server manually (As in installing apache, then php, then mysql, rather than xampp).

You can find some tutorials of doing this at ubuntuguide.org

---

### Post by Mirrorball on 2007-05-13
```
sudo apt-get install apache2 libapache2-mod-php5 mysql-server php5-mysql
```Or install these packages from Synaptic. No need to download xampp or compiling anything.

---

### Post by AdamG on 2007-05-13
> **Mirrorball said:**
> ```
sudo apt-get install apache2 libapache2-mod-php5 mysql-server php5-mysql
```Or install these packages from Synaptic. No need to download xampp or compiling anything.Seconded. Using Ubuntu's package management should always be preferred, all other things equal, since they allow for automatic security updates, easier dist-upgrades and better integration.

---

### Post by adam93250 on 2007-05-14
Ok, the apt-get seems to have installed them all, but do you have any GUI Control suggestions?
Simply, any GUI programs I can use to control the webserver and all of its features.

---

### Post by adam93250 on 2007-05-14
Ok, i used the code above to get the server files, and the server runs and can be accessed.

One problem. I dont have a clue where the files have been placed.
Could anyone tell me where?


Also, a good GUI/WEB Control Interface would be nice. If anyone can help me install phpMyAdmin?

---

### Post by Mirrorball on 2007-05-14
The files are placed in /var/www and phpMyAdmin can be installed by typing in a terminal:
```
sudo apt-get install phpmyadmin
```

---

### Post by adam93250 on 2007-05-14
i really should of thought about that.
I found the files, and have made a 'Public' directory so i can edit files.

Just one problem though, php5 does not seem to be running.
When i goto [http://myip](http://myip) i get the apache files listing, so its fine.
However, When i goto [http://myip/phpmyadmin](http://myip/phpmyadmin) nothing happens.

So, i could do with a way to re-install php5, to a working state.

---

### Post by adam93250 on 2007-05-14
seems i already had phpmyadmin installed.
AND php5 says its already at the latest version.

Anymore ideas why PHP is not running?

---

### Post by adam93250 on 2007-05-14
Ok, i am totally confused.

Can someone give me an easy way to check PHP5, MySQL5 for their validity?
Once i know if they are valid, i want to know how to setup a database here, i dont think it actually has setup a database.

---

### Post by Mirrorball on 2007-05-14
Restart Apache first.
```
sudo /etc/init.d/apache2 restart
```
If it doesn't work, go to /etc/apache2/mods-enabled (or something like that) and see what files are there. There should be a file with 'php' in the name.

---

### Post by adam93250 on 2007-05-14
```
adam@laptop:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
^[[Aapache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
adam@laptop:~$ sudo /etc/init.d/apache2 restart

```

I have php5.conf and php5.load in that folder.

---

### Post by Mirrorball on 2007-05-14
:( I'd go to Synaptic, mark apache2 for complete removal, apply, and install it again. If it was "Unable to open logs," we can't even read the logs to find out what's wrong. Maybe you tried to install Apache some other way and left configuration files behind.

---

### Post by adam93250 on 2007-05-14
nope, you game me the apt-get information and thats what i used.
Ok, everything that was installed that came under apache2, has been 'completely removed'

I would believe you know what i am trying to get here, so could you perhaps give some more apt-get codes? i dont mind using synaptic, as long as you give me the EXACT package name

---

### Post by Mirrorball on 2007-05-14
It's apache2.

---

### Post by adam93250 on 2007-05-14
yes, but do i need any of the others to get PHP and MySQL to run?

---

### Post by Mirrorball on 2007-05-14
Yes, you need all of these: apache2, libapache2-mod-php5, mysql-server, php5-mysql.

---

### Post by adam93250 on 2007-05-14
Ok, i have downloaded them all through synaptic, is there anything i should do before i run my first test?

---

### Post by adam93250 on 2007-05-14
Ok, here is the bottom of the Page

Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 192.168.1.72 Port 80

Here is the page

```
Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 20:16 	-
[DIR]	phpmyadmin/	24-Mar-2007 23:47 	-
[DIR]	public/	14-May-2007 18:20 	-
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 192.168.1.72 Port 80

```

---

### Post by adam93250 on 2007-05-14
phpmyadmin re-installed

Still, when i goto the index.php page, it doesn't load, it asks to download.

---

### Post by Mirrorball on 2007-05-14
I think everything is OK. Install phpmyadmin like you did before and it should work. (It was uninstalled when you uninstalled apache.)

---

### Post by adam93250 on 2007-05-14
i have re-installed it, it appears in the apache web directory.

Problem is, the files always ask to download, they never open in firefox.

WOW!!!!!
IT WORKS!!!!!!

Thankyou so much, its really nice to have friendly people like you around to help people like me.
If i have any other questions, ill let everyone know.

---

### Post by Mirrorball on 2007-05-14
I can't connect, maybe your firewall or ISP is blocking it. But clean your browser's cache.

---

### Post by adam93250 on 2007-05-14
wait.
Whats the password to phpmyadmin??
the default password?

sorry, gave you my internal, this is the right one [http://88.107.152.49](http://88.107.152.49)

---

### Post by interval1066 on 2007-05-14
you might want to disable directory listings now, and deny access to phpmyadmin outside of your firewall or even local host. You've got a severely open wound there...

---

### Post by adam93250 on 2007-05-14
i know, i need to setup a login system so that i can access the files away from home.

But for now, its on a computer that goes offline often.

Thanks for all your help.

---

### Post by Mirrorball on 2007-05-14
> **adam93250 said:**
> 
Whats the password to phpmyadmin??
the default password?

root as a username, blank password.
> **adam93250 said:**
> sorry, gave you my internal, this is the right one [http://88.107.152.49](http://88.107.152.49)
I should have noticed. But a blank password should work.

---

### Post by adam93250 on 2007-05-15
Ok, ill try the blank password, then change it.

I said i was going to setup a login to allow me to access those files, this can be done in apache?
Could you tell me how to do it in apache?

---

### Post by adam93250 on 2007-05-15
Ok, blank password worked, and password has now been changed.
All i need now is to protect the directory.

On the permissions page, it has 5 users.

There is Any, debian, root, root, root
```
Any  	%  	--  	 USAGE
debian 	localhost 	Yes 	SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, REPLICATION SLAVE, REPLICATION CLIENT, EXECUTE
root 	127.0.0.1 	Yes 	ALL PRIVILEGES
root 	laptop 	Yes 	ALL PRIVILEGES
root 	localhost 	Yes 	ALL PRIVILEGES 
```

Looking at that, i would of thought i am the only one who CAN access the admin. I must be wrong.

---

### Post by Mirrorball on 2007-05-15
```
Any  	%  	--  	 USAGE
```
Anyone has USAGE privileges.

---

### Post by adam93250 on 2007-05-15
Usage of data? or Usage of phpadmin?

I need to setup a mail server as well. Help, Please.

---

### Post by adam93250 on 2007-05-15
i just thought.

Every user does not need to access any data.
The web apps have their own users, so 'anyone' doesnt have to access anything in MySQL databases.

I've removed 'any'

---

### Post by adam93250 on 2007-05-15
_So, mail server._
I need the mailsever so i can use it for all my internal emails.

_Also, password protect directory listings._
I still see it possible to access the directory listing, but i want to have access with a password.
So, Anyone who doesnt know the password will get an error message.

_And, Protecting phpmyadmin._
I was able to access myadmin at my school, which should not be allowed.
Really i do want to be able to access it remotely, but would like it so that only people who had the password could reach the login screen.
Yes, the only way to access the admin at the moment is to know the full URL, but i would still like password-security.

**------------------------------------------------------Additional Notes------------------------------------------------------**

Any help on any of these issues would be fine.
Terminal or Synaptic, either works, just give me the full package name of the main AND extra files i would need.

_Setting up._
If there is  small configuration needed, either give me Terminal code, OR a guide to another way.

_Future Config._
I would like a GUI to ALL web-apps i install for ease of configuration/updates.

Thats just about everything, thanks in advance to all help.
**-------------------------------------------------________()________-------------------------------------------------**

---

### Post by adam93250 on 2007-05-15
Ok, any help would be apreciated.

I have started a webhosting service, so i could do with having those 3 things solved as soon as i can. Thanks.

---

### Post by adam93250 on 2007-05-31
Ok, changing things for a bit.
I have had to setup my webserver on my Windows machine (Linux one broken)
The only problem i have at the moment is logging in to phpMyAdmin.

I have setup the 'config.inc.php' through the web interface, and follwed the instruction of moving it to top-level directory and deleting the 'config' folder.

Problem is, it wont even let me log on.
It says access denied, before it even lets me type a password!

Anyone know what i can do?

WebServer Applications
PHP 5 (Latest)   MySQL 5 (Latest)   Apache 2.0 (Compatible)

-------------------------------------------------------------------------------------------------------------------------------------

Also, could someone just see if they can access my site? Thanks.
goto [http://ashosting.info](http://ashosting.info) and click the link at the bottom of the screen.

---

### Post by adam93250 on 2007-06-01
Ok, another question.

I need the 'password protect directory' feature for apache, can someone explain this?

Also, when i goto my folders it does not redirect to the index.php file, which it should.

If anyone can help me with this, post.

---

### Post by adam93250 on 2007-06-02
ok, sorted the phpmyadmin problem, but does anyone know how to password protect folders?
And it still does not show me the index.php/html when i goto a directory.

If you need any information from me, just ask your question and i will give you an answer.

---


---
title: "Why can't I run PHP scripts in Firefox/Ubuntu?"
date: 2009-08-08
forum: Programming Talk
---

### Post by poubelle on 2009-08-08
Hello all,

I was a Mac user for a decade before switching to Ubuntu this year. In my Web development work,  I often tested my PHP scripts locally. I don't recall having any special setup for this... nothing that I had to struggle to set up, anyway. (It's been a few years so I don't remember.)

Now, in Firefox on Jaunty, I can't run any PHP. Firefox just asks me to download the file or choose a program to open with. I try selecting Firefox as the program to open them with, but it just returns me back to the dialog box. This is true even when the PHP file basically just echoes HTML. I have to upload everything before testing.

I've installed PHP... what more do I need to do?

Is this a question better asked at the Firefox forums?

Help!

---

### Post by wojox on 2009-08-08
Edit your httpd.conf put in 
```
AddType application/x-httpd-php .php .htm .html
AddType application/x-httpd-php-source .phps 
```

Restart Apache

```
sudo /etc/init.d/apache2 restart
```

Clear your firefox cache

Hope that helps.

---

### Post by rohitvk on 2009-08-08
i had the same problem.
i did this

$ sudo apt-get install libapache2-mod-php5  

(installed it)

then enable it by
$ sudo a2enmod php5

then restart apache by
sudo /etc/init.d/apache2 restart


then if you get error like, 

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

try this

$ echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

(just adding the second part coz I got this error too along with the 1st one)

---

### Post by poubelle on 2009-08-08
> **rohitvk said:**
> i had the same problem.
i did this

$ sudo apt-get install libapache2-mod-php5  

(installed it)

then enable it by
$ sudo a2enmod php5

then restart apache by
sudo /etc/init.d/apache2 restart


then if you get error like, 

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

try this

$ echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

(just adding the second part coz I got this error too along with the 1st one)

Hmm... it looks like this is already installed and enabled:

```
julie@jubuntu:~$ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
libapache2-mod-php5 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
julie@jubuntu:~$ sudo a2enmod php5
Module php5 already enabled
```

> **wojox said:**
> Edit your httpd.conf put in 
```
AddType application/x-httpd-php .php .htm .html
AddType application/x-httpd-php-source .phps 
```

Restart Apache

```
sudo /etc/init.d/apache2 restart
```

Clear your firefox cache

Hope that helps.

I'll try this... httpd.conf isn't where I expected it to be though. (/etc/httpd/conf) Trying to find it...

Thanks to you both for replying!

---

### Post by wojox on 2009-08-08
Should be in /etc/apache2/

---

### Post by poubelle on 2009-08-08
OK. I added the AddTypes to httpd.conf and restarted Apache. I got the error rohitvk mentioned about the fully qualified domain name, so I used that command to name it Localhost. Then I restarted Apache again. But still I get asked to download PHP files. 

I tried running them from my usual directory (in my home dir) and from /var/www but nada.

---

### Post by wojox on 2009-08-08
Did you clear out firefox?

---

### Post by poubelle on 2009-08-08
Yep... through Firefox's preferences dialog, then restarted FF. Still the same situation. Is there another place I should clear the cache, like emptying a directory or something?

There was nothing else in httpd.conf when I added those lines... is that normal? 

I feel like there must be something huge that I'm just missing.

---

### Post by wojox on 2009-08-08
Yes it' normal. Is your php script in /var/www/

---

### Post by poubelle on 2009-08-08
Yep, I tried running it from /var/www.

---

### Post by wojox on 2009-08-08
Look in /var/log/error.log see if it gives us any hints.

---

### Post by jeffathehutt on 2009-08-08
How exactly are you trying to run the scripts?  You should be able to point firefox to [http://localhost/script.php](http://localhost/script.php) assuming you put the script in /var/www and it should work.  Make sure you are accessing the files through apache.  Firefox itself has nothing to do with the script actually running, that is apache's job to run it, so I doubt Firefox is the problem.

---

### Post by Can+~ on 2009-08-09
Change the permissions on the files on the /var/www to Group read and change the group to www-data.

Then try to connect to [http://127.0.0.1](http://127.0.0.1) or [http://localhost](http://localhost)

---

### Post by poubelle on 2009-08-09
> **wojox said:**
> Look in /var/log/error.log see if it gives us any hints.

There isn't one... no error.log in /var/log, that is. I guess this means Apache isn't set up/installed completely?

> **jeffathehutt said:**
> How exactly are you trying to run the scripts?  You should be able to point firefox to [http://localhost/script.php](http://localhost/script.php) assuming you put the script in /var/www and it should work.  Make sure you are accessing the files through apache.  Firefox itself has nothing to do with the script actually running, that is apache's job to run it, so I doubt Firefox is the problem.

OK. This is interesting.

I have been trying to load them by dragging them onto an open Firefox window, or by right-clicking and selecting "Open in Firefox". This is what I did for 9+ years on the Mac (directly from my home directory) so I didn't think I needed to do otherwise.

So, Firefox *does* load PHP scripts directly on at least one other platform.

That being said, I tried via [http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1) and I get a "can't establish connection" error from FF. Again, looks like Apache's not quite there?

> **Can+~ said:**
> Change the permissions on the files on the /var/www to Group read and change the group to www-data.

Then try to connect to [http://127.0.0.1](http://127.0.0.1) or [http://localhost](http://localhost)

This is what the file was already:

```
-rw-r--r--  1 root root 3404 2009-08-08 11:57 index.php
```

I chowned to www-data and chmodded to 755 for the hell of it:

```
-rwxr-xr-x  1 www-data root 3404 2009-08-09 10:56 index.php
```

FWIW, still the same "can't establish a connection" error.

I fear this is something really stupid and I'm going to get rocks thrown at me for troubling everyone over it...

---

### Post by Can+~ on 2009-08-09
Don't use chown, that changes the owner, not the group. Change the owner back to you and use chgrp to change the group to www-data.

Second, put an index.html inside and see if it's apache or php the problem.

Another thing, Firefox is not supposed to parse PHP when working on web programming. PHP is interpreted server-side, therefore, it must reside inside a folder which can be accessed by apache2.

If you still have problems, here's a full summary of what you need to do:

[list=1]
[*] Install apache2 libapache2-mod-php5 (The other dependencies will be downloaded automatically)
[*] You don't need to edit the /etc/apache2, the defaults already work.
[*] Place a file named index.php (or .html) on the /var/www/ folder.
[*] Change the permission to ???r--??? (being ??? whatever you want, I usually do rw-r----- (640))
[*] Change the group to www-data
[*] Open firefox on 127.0.0.1 or localhost (loop-back address (your machine))
[/list]

---

### Post by poubelle on 2009-08-10
> **Can+~ said:**
> Don't use chown, that changes the owner, not the group. Change the owner back to you and use chgrp to change the group to www-data.

Oh yes, you're right -- I did fix that though, and nothing changed.

> **Can+~ said:**
> Second, put an index.html inside and see if it's apache or php the problem.

It works when viewed via **file:///var/www/index.html** but not via **[http://localhost/index.html](http://localhost/index.html)** or via **[http://127.0.0.1/index.html](http://127.0.0.1/index.html)** (those return connection errors).

> **Can+~ said:**
> Another thing, Firefox is not supposed to parse PHP when working on web programming. PHP is interpreted server-side, therefore, it must reside inside a folder which can be accessed by apache2.

I'm not sure exactly what you're getting at here. I know that PHP scripts are interpreted/executed by the PHP runtime, not executed client-side like (say) Javascript. But I'm not sure if that was what you were trying to say or not. 

Maybe this is what you were addressing: I was just saying that I was always able to test PHP files in my browser locally when I used OS X, whether or not they were located in the "web sharing" folder. (In fact I almost always had Web sharing turned off.) 

The title of my post is perhaps misleading, then; I should have said "view PHP scripts" or "test PHP scripts", but just for the record I do know Firefox is not itself executing them.

> **Can+~ said:**
> If you still have problems, here's a full summary of what you need to do:

[list=1]
[*] Install apache2 libapache2-mod-php5 (The other dependencies will be downloaded automatically)
[*] You don't need to edit the /etc/apache2, the defaults already work.
[*] Place a file named index.php (or .html) on the /var/www/ folder.
[*] Change the permission to ???r--??? (being ??? whatever you want, I usually do rw-r----- (640))
[*] Change the group to www-data
[*] Open firefox on 127.0.0.1 or localhost (loop-back address (your machine))
[/list]

libapache2-mod-php5 was already at the most recent version, so apt-get wouldn't install it, but it did let me install apache2... so I did that.

Still can't connect to server.

(I chmodded the two files to 777 just for the hell of it, for testing.)

Here's what's in /var/www:
```
julie@jubuntu:/var/www$ ls -al
total 16
drwxr-xr-x  2 root root     4096 2009-08-09 10:56 .
drwxr-xr-x 16 root root     4096 2009-06-13 23:28 ..
-rwxrwxrwx  1 root www-data   45 2009-06-13 23:29 index.html
-rwxrwxrwx  1 root www-data 3404 2009-08-09 10:56 index.php
```

Apache is installed:
```
julie@jubuntu:/var/www$
/usr/sbin/apache2
```

But still... same deal.

However, then I tried this for kicks:
```
julie@jubuntu:/var/www$ php index.php
The program 'php' is currently not installed.  You can install it by typing:
sudo apt-get install php5-cli
```

I did install PHP (and MySQL and Apache) just a couple of weeks ago, but maybe the wrong packages?! Wrong versions or something?

Anyway, I've (re?) installed it, and now I can get index.php to output at the command line and (after restarting Apache) via [http://localhost](http://localhost). (I still get the download dialog if I try to load them from my home folder, but I'll take what I can get. I'll just move all my dev stuff into /var/www I guess.)

Incidentally, I chgrped both files back to root and they load fine that way... just for future reference.

**Thanks for all your help!**

---

### Post by J_dillinger on 2009-08-11
Both of those methods may work, but setting up an apache server is simple.  use Synaptic or apt-get install apache2 to set up apache2 on the system you might want to install and configure mysql at the same time to integrated databases into your php scripts.  After installing Apache2 you will need to configure apache2.conf to allow php.  You can use text editors like vi or nano, but I like gedit with the GUI installed.

sudo gedit /etc/apache2/apache2.conf
(Note: Depending on the version of ubuntu you might have to edit /etc/httpd/httpd.conf)

Look through the file and make the following changes...


</Directory>

#
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    DirectoryIndex **index.php** index.html
</IfModule>

add index.php to the directory index so the web browser will load the page when you access the loopback address - 127.0.0.1.

While I don't  see it the apache2.conf file on my fedora box I also had to uncomment (remove the # sign before the line) to allow the use of the php module.  If php does not function check to make sure it is availableX.  Depending on how you performed the ubuntu install also check for httpd.conf in the apache directory and in /etc/httpd/httpd.conf.  The two files are very similar, but in 9.04 httpd.conf is an empty file that has to be included into /etc/apache2/apache2.conf.

There you go, the power of the web at your finger tips....

---


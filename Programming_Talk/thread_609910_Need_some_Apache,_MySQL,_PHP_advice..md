---
title: "Need some Apache, MySQL, PHP advice."
date: 2007-11-11
forum: Programming Talk
---

### Post by Griff on 2007-11-11
I'm very new to sql and php.  To get started I could use a little newbie advice.  

First, what I need to do:  I need to create a website that is able to take input from users and query a database for the results.  This brings me to a lamp.  To install everything I need to get started I should only need to do the following right?
```
sudo tasksel install lamp-server
```
After this is installed what do I need to add to my startup so everything is running on boot?

Next, I looked over phpmyadmin and it looks pretty useful.  Would I be able to use this outside my network to work on the database/everything else?

Thanks,
Griff

---

### Post by Kadrus on 2007-11-11
```
sudo apt-get install apache2

```
Then type in your url:
[http://localhost](http://localhost) 
to see if it works
For Php5
```
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```

Test if it is installed correctly:
```
gksudo gedit /var/www/testphp.php
```
Insert this into the file
```
<?php phpinfo(); ?>
```
Save it
then open 
[http://localhost/testphp.php](http://localhost/testphp.php)

That it is for installing Apache and PHP5..
To install MySql for Apache type:
```
sudo apt-get install libapache2-mod-auth-mysql
```
That's pretty much it for creating databases..hope that helped :)

---

### Post by mkoehler on 2007-11-11
Griff,

     As for phpmyadmin, yes, you can use it from outside your network in order to visually run SQL commands on the database.  However, in order to make your webserver visible from outside of the network, you will need to (at a minimum) forward all requests on port 80 (or 8080, depending on your apache2 configuration) to the internal (network) IP of the server.  If you need more help on getting this set up, I'd be happy to help you.

Cheers!

---

### Post by Hopworks on 2007-11-11
> **Griff said:**
> I'm very new to sql and php.  To get started I could use a little newbie advice.  

First, what I need to do:  I need to create a website that is able to take input from users and query a database for the results.  This brings me to a lamp.  To install everything I need to get started I should only need to do the following right?
```
sudo tasksel install lamp-server
```
After this is installed what do I need to add to my startup so everything is running on boot?

Next, I looked over phpmyadmin and it looks pretty useful.  Would I be able to use this outside my network to work on the database/everything else?

Thanks,
Griff
Is it really that easy??
Sigh
Something must have went wrong with my LAMP install when I installed Ubuntu 7.04 Server. Nothing I was supposed to be preconfigured with was there, so I did all the LAMP components separately via apt-get and spm. I was real new to Linux then, still am but not as new, so I probably didn't do something I needed to. Anyway, lots of configuring later, and using webmin, I'm where I want to be with a LAMP on my LAN.

But it was NEVER as easy as  ```
sudo tasksel install lamp-server
``` for me. I learned a lot doing it manually though, and it was a fun ride. :)

---

### Post by LaRoza on 2007-11-11
> **Hopworks said:**
> Is it really that easy??

But it was NEVER as easy as  ```
sudo tasksel install lamp-server
``` for me. I learned a lot doing it manually though, and it was a fun ride. :)

Starting with Feisty, yes.

---

### Post by Griff on 2007-11-11
Alright, it all looks good right now.  I'm sure I'll have issues soon.  Thanks so far, everyone!
--Griff

---

### Post by Griff on 2007-11-11
How do I run phpmyadmin? I installed it but it isn't an application option and ```
phpmyadmin
```doesn't work either.

---

### Post by aks44 on 2007-11-11
phpMyAdmin is web-based. On stock installs it is located at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by Griff on 2007-11-11
> **aks44 said:**
> phpMyAdmin is web-based. On stock installs it is located at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
Not there for me. I just installed through apt. :confused:

---

### Post by aks44 on 2007-11-11
Check in /var/www/ there should be a symlink to it (which should point to /usr/share/phpmyadmin/).

If it isn't there, your install probably went wrong at some point.

---

### Post by Griff on 2007-11-11
> **aks44 said:**
> Check in /var/www/ there should be a symlink to it (which should point to /usr/share/phpmyadmin/).

If it isn't there, your install probably went wrong at some point.
Something seems to have gone wrong then I suppose.  There's no symlink in /var/www/ or a /usr/share/phpmyadmin/ directory.  I'm going to try to uninstall and reinstall.
edit: no luck, still no where to be found

---

### Post by nbv4 on 2007-11-12
> **Kadrus said:**
> ```
sudo apt-get install apache2

```
Then type in your url:
[http://localhost](http://localhost) 
to see if it works
For Php5
```
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```

Test if it is installed correctly:
```
gksudo gedit /var/www/testphp.php
```
Insert this into the file
```
<?php phpinfo(); ?>
```
Save it
then open 
[http://localhost/testphp.php](http://localhost/testphp.php)

That it is for installing Apache and PHP5..
To install MySql for Apache type:
```
sudo apt-get install libapache2-mod-auth-mysql
```
That's pretty much it for creating databases..hope that helped :)

How do you install mysql for PHP? I followed your steps, but now whenever I try to run a php script with mysql commands, I get:

Resolving a Fatal error: Call to undefined function mysql_connect()

which google leads me to believe I need to install something to get PHP to understand mysql stuff.

EDIT: nevermind, I found the answer: sudo apt-get install php5-mysql

---

### Post by Kadrus on 2007-11-12
> **Griff said:**
> Not there for me. I just installed through apt. :confused:

Try this :
```
sudo apt-get install libapache2-mod-auth-mysql
```

then type this :
```
 sudo apt-get install php5-mysql

```

then this:
```
sudo apt-get install phpmyadmin
```

The get PHP working with MYSql :

```
gksudo gedit /etc/php<version>/apache2/php.ini

```

Uncomment the extension that looks like this ";extension=mysql.so"
It should become like
```
 
 ...
extension=mysql.so
...


```

Save the file 
type 

```
http://localhost/phpmyadmin
```

If it runs.. Party :)..
Hope that worked..

---

### Post by Kadrus on 2007-11-12
> **nbv4 said:**
> How do you install mysql for PHP? I followed your steps, but now whenever I try to run a php script with mysql commands, I get:

Resolving a Fatal error: Call to undefined function mysql_connect()

which google leads me to believe I need to install something to get PHP to understand mysql stuff.

EDIT: nevermind, I found the answer: sudo apt-get install php5-mysql

Or if you want follow the steps in the post below..but I think it worked anyway because your answer is included down there too :):)

---

### Post by Kadrus on 2007-11-12
> **nbv4 said:**
> How do you install mysql for PHP? I followed your steps, but now whenever I try to run a php script with mysql commands, I get:

Resolving a Fatal error: Call to undefined function mysql_connect()

which google leads me to believe I need to install something to get PHP to understand mysql stuff.

EDIT: nevermind, I found the answer: sudo apt-get install php5-mysql

And to test if PHP is working type this...I assume you already have..but just in case:
```
<?php
$con = mysql_connect("localhost","yourusername","yourpassword");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }



?>


```

---

### Post by Griff on 2007-11-13
Well, I've tried everything mentioned above about getting phpmyadmin working, but I am still unable to run it.  I know php is working because my testphp.php file works properly.  I installed phpmyadmin twice but I still can't find where it installs to.  Any ideas on where it is or how to get it working?  This is really frustrating since all the other pieces seem to be working but this useful tool isn't.
Thanks,
Griff

---

### Post by Kadrus on 2007-11-13
> **Griff said:**
> Well, I've tried everything mentioned above about getting phpmyadmin working, but I am still unable to run it.  I know php is working because my testphp.php file works properly.  I installed phpmyadmin twice but I still can't find where it installs to.  Any ideas on where it is or how to get it working?  This is really frustrating since all the other pieces seem to be working but this useful tool isn't.
Thanks,
Griff

Euuh..Griff..most of the time when it doesn't work I think it's because of the part where you have to comment the thing 
Check it one more time and make sure it looks like this:

...
extension=mysql.so
...


It should look exactly like this in Gedit..

Try again and hopefully it will work :)

---

### Post by Griff on 2007-11-13
Ok.  I found where phpmyadmin installed to, which is /etc/phpmyadmin.  Any ideas on how to make it work?

---

### Post by Kadrus on 2007-11-13
> **Griff said:**
> Ok.  I found where phpmyadmin installed to, which is /etc/phpmyadmin.  Any ideas on how to make it work?

Did you go to 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

I think it's supposed to work..

---

### Post by Griff on 2007-11-13
> **Kadrus said:**
> Did you go to 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

I think it's supposed to work..
I did, it doesn't work.  There's supposed to be a symlink in /var/www which I don't have which makes [http://localhost/phpmyadmin](http://localhost/phpmyadmin) work.  Problem is I don't know how to make said link or what it links to.  :(

---

### Post by smartbei on 2007-11-13
See [http://www.ss64.com/bash/ln.html](http://www.ss64.com/bash/ln.html)

You want a symbolic link, so use the -s option.

As far as I know it links to /etc/phpmyadmin

---

### Post by aks44 on 2007-11-13
*If* you have /usr/share/phpmydamin/ then you can make the link yourself:

```
$ sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```


> **smartbei said:**
> As far as I know it links to /etc/phpmyadmin
On my comp (Feisty) it links to /usr/share/phpmyadmin/
/etc/phpmyadmin/ just contains config files (as it should), not the portal itself.


EDIT: at this point, I would advise you to uninstall *everything* related to apache / php / mysql / phpmyadmin (including manually removing the relevant config folders in /etc/) and try tasksel again. As far as I'm concerned it always worked fine on Feisty, so unless the Gutsy packages are broken there is no reason that it shouldn't work.

---

### Post by Kadrus on 2007-11-13
> **Griff said:**
> I did, it doesn't work.  There's supposed to be a symlink in /var/www which I don't have which makes [http://localhost/phpmyadmin](http://localhost/phpmyadmin) work.  Problem is I don't know how to make said link or what it links to.  :(

Unfortunately I don't think I can help you anymore :(..
All I can say is retry those steps and good luck..
Try Searching it in Google..maybe something will come up..
Hopefully..

---

### Post by Griff on 2007-11-13
> **aks44 said:**
> *If* you have /usr/share/phpmydamin/ then you can make the link yourself:

```
$ sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```



On my comp (Feisty) it links to /usr/share/phpmyadmin/
/etc/phpmyadmin/ just contains config files (as it should), not the portal itself.


Creating that link worked.  I was able to open up phpmyadmin and log in.  Thanks for all the help!
Griff

---

### Post by smartbei on 2007-11-13
> **aks44 said:**
> On my comp (Feisty) it links to /usr/share/phpmyadmin/

My mistake. Ok, too many mistakes (minor ones at least) in a row. From now on, will only post from the Ubuntu computer at home from which I can verify these things :).

EDIT: Glad to see it worked out for you Griff.

---

### Post by aks44 on 2007-11-13
> **smartbei said:**
> My mistake. Ok, too many mistakes (minor ones at least) in a row. From now on, will only post from the Ubuntu computer at home from which I can verify these things :).
I tend to be quite useless if I can't verify things, so kudos to you since your "mistakes" are quite minor indeed IMO for someone who is working from the top of his/her head.


> **Griff said:**
> Creating that link worked.  I was able to open up phpmyadmin and log in.  Thanks for all the help!
Glad to see you finally sorted this out. :)

---

### Post by kefler on 2007-11-15
Setting up a server in ubuntu server 7.04 in "english" terms.

In a terminal window type in or copy and paste(use shift+ins to paste in a terminal window/command line environment)

> 
sudo aptitude install apache2 mysql-server mysql-client php5 php5-mysql libapache2-mod-auth-mysql phpmyadmin

[enter your root password]

by default, this will be widely available to the web assuming you're not running through a router.

if you're a nubby to network as well and have no idea what a router is,..

type in:
> sudo ifconfig

this will display a lot of mumbo jumbo(all your network interfaces and the ipv6+ipv4 addresses assigned to them)

the one you want is probably the last one which is connected to the "net"

the second last or laste line should be the ipv4 IP address(ignore the technical mumbo jumbo if you don't understand it) and just look for a 192.168.x.x
if you find it, then you're running through a router and you can ask the previous guy for help with port forwarding, if not, then everything should work fine after the install.

As for accessing  your phpmyadmin outside of your network, I strongly suggest against this as phpmyadmin does NOT have any ban rules set for password attempts to your mysql server, while accessing your phpmyadmin page outside of your network is easly done with 1 command, there is still the security issue.

If you absolutely need to access your server  configurations outside  of your local network, try cpanel or webmin(i suggest webmin as I had trouble installing cpanel on ubuntu.)

For webmin, google webmin, it should be the first link, download the debian package to your desktop, and execute the follow command:

> cd Desktop
sudo dpkg -i webmin-1.380_all.deb

When you go to install webmin from a fresh install of ubuntu it will scream about the missing dependencies, once this does, it'll prompt you to remove webmin, just quit(enter "q" without quotes and press enter)

with that done, the list of dependencies should still be on screen.
take note of these and run:
> sudo aptitude install ___________
for each of the dependency

after you have installed all the dependencies(after the very last one)
webmin setup will kick back up and continue with it's installation by itself.

The webmin setup should require no or very little input from you.
once the webmin install is done, navigate your browser to > [https://localhost:10000](https://localhost:10000) , accept the certificate (make sure it's from your server) and login with your account details(your current user) and voila a fully functional remote administration system that is password protected and can do more than just allow you to admin your mysql databases =) and it's safe !!!

I hope this wasn't too confusing >.< I'm new to linux so I know it can be confusing. i'm pretty sure everything i've said here was in plain enough english :confused::lolflag:

---

### Post by aks44 on 2007-11-15
> **kefler said:**
> sudo aptitude install apache2 mysql-server mysql-client php5 php5-mysql libapache2-mod-auth-mysql phpmyadmin

IIRC the **apache2** package installs by default the **apache2-mpm-worker** package (at least on Feisty, it may have changed with Gutsy but I guess not), which *doesn't* work with **libapache2-mod-php5** (required by the **php5** package).

What you need to use is **apache2-mpm-prefork**.

So instead of manually install packages using aptitude / apt-get, better use **tasksel** which will *correctly* install whatever is needed.

---

### Post by kefler on 2007-11-16
No, you are correct, it hasn't changed in gusty, but like I said I'm new to linux and I'm still finding my way around the system. I dislikes using things if I don't know what they do, ie. batch jobs (ie. tasksel) if I did not write it myself or I know exactly what it will do/install (with the exception of apt-get/aptitude which handles most of your required dependencies for you. I tried doing this manually in redhat and it was a nightmere, so never again will I try to do the job of apt.)

With that said, weather you use apt-get or aptitude, when apt finally gets to install php5 and reconfiguring your apache confs and what not, the apache2-mpm-worker package originally installed with apache2 will get removed and the dependencies for php5 will be installed.

I came over to linux without a shred of information on how to actually use it and so far, a lot of the things I used to do in windows are easier done in linux. Installing software now only requires me to enter a command or two(most of the time unless it requires configuration+compiling) where as windows there is an "intuitive setup process which I wish weren't so "intuitive" and more streamlined  like apt =) So far, aptitude and apt-get haven't failed me yet, so until they do, I will not be trying anything new to install the packages I want(personal preference and not recommended to others, exploration is the key to learning after all) Ok, there was a point to this little rant but i forgot it part way through....

---

### Post by aks44 on 2007-11-16
> **kefler said:**
> when apt finally gets to install php5 and reconfiguring your apache confs and what not, the apache2-mpm-worker package originally installed with apache2 will get removed and the dependencies for php5 will be installed.

Whoops. libapache2-mod-php5 indeed requires apache2-mpm-prefork which conflicts with apache2-mpm-worker. Thanks for the correction!

---

### Post by Mr K on 2007-11-16
ok... I've done all you mumbo jumbo stuff but I still can't view php pages on my apache.. When i open them in localhost apache just wants me to download them. I really don't understand what is missing!

---

### Post by Kadrus on 2007-11-16
> **Mr K said:**
> ok... I've done all you mumbo jumbo stuff but I still can't view php pages on my apache.. When i open them in localhost apache just wants me to download them. I really don't understand what is missing!
Are you sure you are opening them from localhost?
Because if you wrote a PHP code and saved it on your desktop that will happen..but if you saved it in the directory /var/www/ i don't think it will..
Weird...

---


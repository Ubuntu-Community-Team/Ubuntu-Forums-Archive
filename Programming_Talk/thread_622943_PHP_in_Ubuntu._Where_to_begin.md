---
title: "PHP in Ubuntu. Where to begin?"
date: 2007-11-25
forum: Programming Talk
---

### Post by foolios on 2007-11-25
I found a thread that gave the command to install apache with a php module.
Seemed like that worked.

The command to test it didn't work as I don't think it was in the right format. So, hopefully it's set up right.

Where is the root directory of the apache folder for storing my php pages?
What free editor can I use for editing php within ubuntu?

Thanks in advance.

---

### Post by geirha on 2007-11-25
Web root is in /var/www/ if I remember correctly.

Bluefish is often mentioned, you might give that editor a try.

---

### Post by ThinkBuntu on 2007-11-25
For your free editor, you have two great choices:

[LIST=1]
[*]GEdit: Very solid editor with support for all verieties of syntax highlighting, can be made to complete code, etc. very well. Nice file pane too
[*]Vim: Higher learning curve, but masters of this editor have ridiculously good productivity
[/LIST]

Both come installed. Install the gedit-plugins (check Synaptic) to have all the features, and check out the GNOME site for documentation. Install vim-full for the full Vim experience, and edit your .vimrc file to taste.

As for Apache, your sites are located at /var/www

I recommend switching permissions so your user owns this folder, or if you aren't too worried about security do a chmod 777 to it for full writability. I used to symlink /var/www to ~/Sites like on a Mac because that makes things easy for me.

Good luck! PHP is a fun, useful language.

---

### Post by ThinkBuntu on 2007-11-25
Bluefish is good. So is the super-light Geany. I bet Eclipse can be awesome if configured for PHP. For now, you can't go wrong with the default, GEdit since you're probably thinking about the language enough that code completion will get in the way of learning.

---

### Post by ICEcoffee on 2007-11-25
I've just started building my IDE apps in Ubuntu after switching from Deamweaver/WinXP environment. I've spent a lot of time on the forums and Google, and this is where I am:

Requirements: Web development using XHTML, PHP, CSS, Javascript 

Main IDE: Quanta +
Secondary: EasyEclipse (a Java IDE with PHP plugins - not easy to setup)

You will need a 'LAMP' setup if developing for database, best way to install this is via: System> Administration> Synaptic Package Manager.

You can configure Apache to make a folder of your choice, the default folder Apaches serves, ie /home/www/

HTH
Good luck

---

### Post by Kadrus on 2007-11-25
Mmm..well I think you already did the steps that I am going to give you but try  it again anyway:
Open Terminal and Type:
```
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```
Then type this:
```
gksudo gedit /var/www/testphp.php
```
This will open text editor..when it does type this:
```
<?php phpinfo(); ?>
```
Then go to this link
You should see a blue page...something telling you about your server..etc..

And if you want to install MYSQL for Apache HTTP Server
Open Terminal and type :
```
sudo apt-get install libapache2-mod-auth-mysql
```
Then type this:
```
sudo apt-get install php5-mysql
```
Then type :
```
sudo apt-get install phpmyadmin
```
Then type this:
```
gksudo gedit /etc/php<version>/apache2/php.ini
```

There is something that looks like this:
```
;extension=mysql.so
```
Erase it so it can look like this:
```
...
extension=mysql.so
...
```
Save the file and restart Apache 
```
sudo /etc/init.d/apache2 restart
```

Then test
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)


Hope that Helped :)

---

### Post by ThinkBuntu on 2007-11-25
For the phpinfo() example, the URL is [http://localhost/testphp.php](http://localhost/testphp.php)

Thought that might've been unclear. alsto, [http://localhost/](http://localhost/) will show the /var/www folder. You might want to re-map /var/www as your DocumentRoot (Apache's root folder) to a folder of your own making in your Home directory. To do so, look into editing your httpd.conf file.

---

### Post by foolios on 2007-12-01
Thank you, everything seemed to go well.

foo@foo-desktop:~$ gksudo gedit /etc/php5/apache2/php.ini
foo@foo-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                           
Don't know if that could be why I get a 404 error when I try the link to:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Thanks so much for helping me so far. I assumed my <version> was php5. That's what I should have put in place of <version> right?

Thanks

---

### Post by Kadrus on 2007-12-01
> **foolios said:**
> Thank you, everything seemed to go well.

foo@foo-desktop:~$ gksudo gedit /etc/php5/apache2/php.ini
foo@foo-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                           
Don't know if that could be why I get a 404 error when I try the link to:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Thanks so much for helping me so far. I assumed my <version> was php5. That's what I should have put in place of <version> right?

Thanks
yes...

---

### Post by smartbei on 2007-12-01
@foolios:
To fix the error in restarting (which I don't believe is fatal anyway):
> 
gksudo gedit /etc/apache2/apache2.conf

Add the following lines to the end of the file.
> 
#servername fix
ServerName localhost

Save the file, restart apache with:
> 
sudo /etc/init.d/apache2 restart


---

### Post by foolios on 2007-12-05
The file took the two added lines and apache restarted.

Ok this works:
[http://localhost/testphp.php](http://localhost/testphp.php)

and this works:
[http://localhost/](http://localhost/)

But this still gives 404 not found:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Shouldn't there be a phpmyadmin folder visible under /var/www/ ?

---

### Post by foolios on 2007-12-16
I'll have to learn more about this. It's probably a part of fundamentally understanding the process.

---

### Post by LaRoza on 2007-12-16
> **foolios said:**
> 
Shouldn't there be a phpmyadmin folder visible under /var/www/ ?

No, it has its own directory that is aliased.

---

### Post by geirha on 2007-12-17
You can see where phpmyadmin is installed by doing ```
dpkg -L phpmyadmin
``` and /var/www/phpmyadmin should be a symbolic link to the place where it's installed. If you don't have that link, you've probably accidentally removed it or something. Try adding it manually with ```
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

---

### Post by Samjiman on 2007-12-17
This is how best I found to best set up a web server with PHP support.
I prefer Lighttpd over Apache. But its basically very similar to set up. Of course here I am using just a PHP CGI binary for local development. **AFAIK there are extra steps to follow for a secure enough installation for public access.**

1) Install the package for lighttpd. Just do:
```
sudo apt-get install lighttpd
```

Lighttpd seems to start running by itself on system startup and after the initial package install. Navigate to localhost (127.0.0.1) in your web browser to see if its running okay. You should see a place holder page. Documents are served from /var/www.

2) Download the PHP source package from the official PHP website ([http://www.php.net](http://www.php.net)).

3) Extract the source folder somewhere unto your desktop or whatever.

4) Before you build, make sure that you install the developer package for libxml2, this is needed to successfully build (at least the current version) of PHP.
Install like so:

```
sudo apt-get install libxml2-dev
```

5) Navigate into the PHP source folder (in the terminal) you have and configure PHP with the options you need. Or just run ./configure on its own.
```
./configure --enable-fastcgi
``` is what I used for example.

6) After configure completes, you can now build PHP. To build, use
```
make
``` and then install with ```
sudo make install
```.

7) Open up the configuration file for lighttpd (/etc/lighttpd/lighttpd.conf) as root in your text editor of choice. E.g.
```
sudo vim /etc/lighttpd/lighttpd.conf
```.

8 ) Add the mod_cgi module to where the other modules are in the configuration file.
```
mod_cgi
```

9) Add the following to the bottom of the file configuration file.
```

cgi.assign = ( ".php" => "usr/local/bin/php" )

```

10) Save the configuration file and restart the web server.
If all is well, you should now have PHP support.

Here is a simple shell script I have made for starting, stopping and restarting the lighttpd web server. Place it somewhere in your PATH.
Call it something like "webs".

```

#!/bin/sh
# Start, stop, reload or restart lighttpd web server
# (where $1 is "start" or "stop", "reload" or "restart")
sudo /etc/init.d/lighttpd $1

```

HTH. (At least lighttpders) Best of luck.

---

### Post by foolios on 2007-12-17
> **geirha said:**
> You can see where phpmyadmin is installed by doing ```
dpkg -L phpmyadmin
``` and /var/www/phpmyadmin should be a symbolic link to the place where it's installed. If you don't have that link, you've probably accidentally removed it or something. Try adding it manually with ```
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

After doing the search I found it to be at:
file:///usr/share/phpmyadmin/

When I put /usr/share/phpmyadmin in the browser I get an index page for that folder. When I click index.php or main.php it tries to download the page. Even if I click open with firefox it just tries to download it again. It seems like something is amiss with the server not processing the php or something. Everything seems to be up and running just fine though. Maybe I am trying to access phpmyadmin incorrectly. I was thinking that either one of those two pages would lead me to a gui page for working with mysql.

---


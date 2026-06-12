---
title: "Install LAMP for Joomla Development."
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Kev261266 on 2012-10-24
Hi,

I'm totally new to Ubuntu (been using it for two days only) and I've got everything running as need be. My final task to complete the transition from Windows XP to Ubuntu is to install a test server environment for the development of Joomla websites.

In XP I was using XAMPP 1.7.3 (which is not the latest version, but I found it to be the best version for Joomla compatability, particlularly the PHP version 5.3.1) Anyway, I would like to install the same LAMPP stack as XAMPP 1.7.3 on Ubuntu.

I'm not quite sure how to do this. I've studied the following threads:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
and
[http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop](http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop)

The problem is that neither of these guides seem to give options for the PHP version (the Joomla guide states PHP5, but not PHP 5.3.1)

Can anyone suggest how I do the install to get the versions that match Xampp 1.7.3. Just as reference I've listed what versions of what come with Xampp 1.7.3 below.

Another issue I think I will need to address is how do I open sites that I have previously built which have a localhost association in Windows with Xampp, i.e. do I need to move the folders somewhere specific for Ubuntu to associate them with localhost?

In windows I simply installed Xampp on my D: drive and created my site folders in the htdocs folder of the D drive Xampp installation.

I'm pretty sure that this is easily set up in Ubuntu, it's just I don't feel I completely know what goes where at the moment.

Any help would be most appreciated.

Thanks in advance.
-----------------------------------------
As mentioned earlier, here's the Xampp version list:

###### Apache Friends XAMPP (Basis Package) version 1.7.3 ###### 
 
  + Apache 2.2.14 (IPV6 enabled) 
  + MySQL 5.1.41 (Community Server) with PBXT engine 1.0.09-rc 
  + PHP 5.3.1 (PEAR, Mail_Mime, MDB2, Zend) 
  + Perl 5.10.1 (Bundle::Apache2, Apache2::Request, Bundle::Apache::ASP, Bundle::Email, Bundle::DBD::mysql, DBD::SQlite, Randy Kobes PPM) 
  + XAMPP Control Version 2.5.8 (ApacheFriends Edition) 
  + XAMPP CLI Bundle 1.6 
  + XAMPP Port Check 1.5 
  + XAMPP Security 1.1 
  + SQLite 2.8.17 
  + SQLite 3.6.20 
  + OpenSSL 0.9.8l 
  + phpMyAdmin 3.2.4 
  + ADOdb v5.10 
  + FPDF v1.6 
  + Zend Framework 1.9.6 Minimal Package (via PEAR) 
  + Mercury Mail Transport System v4.72 
  + msmtp 1.4.19 (a sendmail compatible SMTP client) 
  + FileZilla FTP Server 0.9.33 
  + Webalizer 2.21-02 (with GeoIP lite) 
  + apc 3.1.3p1 for PHP 
  + eAccelerator 0.9.6-rc1 for PHP 
  + Ming 0.4.3 for PHP 
  + PDF with pdflib lite v7.0.4p4 for PHP 
  + rar 2.0.0-dev for PHP 
  + Xdebug 2.0.6-dev for PHP 
  + libapreq2 v2.12 (mod_apreq2) for Apache

---

### Post by Lars Noodén on 2012-10-24
You'll want to avoid XAMPP to take advantage of the capabilities of Ubuntu's LAMP.  

To get the base, you already have that if you do the following:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Which version of Ubuntu are you running?  12.04 or 12.10?
Version 12.10 has PHP 5.4.6, version 12.04 has 5.3.10.  Perl and python are both already installed and do not need to be added.  

You can see the version if you've installed synaptic and you search for the package name there.  Or you can use apt-cache.

```

apt-cache policy php5
apt-cache policy perl
apt-cache policy apache2
apt-cache policy mysql-server

```

If you've followed the normal procedure for installing Apache, then your files should be in /var/www.  If you are the only user of that server then all you need to do to get write access is to take ownership of the directory.

```

sudo chown -R kev261266 /var/www

```

If you are going to be working with others, then you need to use groups instead.

---

### Post by Kev261266 on 2012-10-25
Hi Lars,

Thank you very much for your assistance on this. I followed your instructions and everything seems to have installed (by the way my installed Ubuntu version is 12.10)

In my browser when I go to localhost I get:

"It Works!
This is the default web page for this server.
 The web server software is running but no content has been added, yet."


I then look in the folder /var/www and I see an index.html file


I then copied one of my existing Joomla site folders into /var/www and entered the address into the browser:


[localhost/designergie_co_uk/administrator/index.php]("http://localhost/designergie_co_uk/administrator/index.php")


where designergie_co_uk is the folder name of the Joomla site.



When I hit refresh I just get a blank page, and not the expected Joomla admin login page.


Not quite sure what to do next :( But I'm pretty sure I'm missing something obvious.


Cheers


Kev

---

### Post by Lars Noodén on 2012-10-25
I don't use PHP any more so hopefully someone who uses it on a daily basis spots your question.  Have you double checked to ensure that the PHP module is installed and active?

```

sudo a2enmod php5

```

If it is not on, then the PHP code will just get interpreted as nothing.

---

### Post by Kev261266 on 2012-10-25
I tried that code and got "module php5 already enabled"

---

### Post by Lars Noodén on 2012-10-25
Ok.  That's a good sign.  

Also to check more obvious things in your virtual host configuration:  What about the [DirectoryIndex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex) directive set to use PHP, too?

```

        DirectoryIndex index.php index.html

```

---

### Post by Kev261266 on 2012-10-25
I input the code and got: DirectoryIndex: command not found

Does that shed any light on the situation?

---

### Post by Lars Noodén on 2012-10-25
It goes in your virtual host's configuration file for Apache.  If you have the default Ubuntu LAMP set up that should be /etc/apache2/sites-available/default

After you make any changes to one of Apache's virtual host configuration files, you should reload the configuration for the changes to take effect.  

```

sudo service apache2 reload

```

---

### Post by Kev261266 on 2012-10-25
I did that code too but still nothing. I do however think I've spotted an issue.

I had another look at this Joomla doc
[http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop](http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop)

and did "1st test for php server" by creating a test file

```
echo "<?php phpinfo(); ?>" | sudo tee /var/www/test.php
```This worked fine and displayed the info as expected. However, when I tried the next step "1st test for phpmyadmin"

by entering localhost/phpmyadmin I get a 404 not found error. The Joomla doc advises me to uninstall lamp and start again from scratch.

Another thing that I think I should point out is that during the installation when I was asked to provide a password for the root dir I just pressed enter and left it blank. Could this be causing the problem?

Do you think I've skipped over something and should start again? Cos I have no clue.

---

### Post by Lars Noodén on 2012-10-25
If test.php worked, then you are most of the way there and it would be counter-productive to reinstall and would not likely solve anything.  This isn't Windows where superstition rules, things should work logically.  

I downloaded Joomla 2.5.7 from the Joomla web site and when I loaded index.php in the web browser, it lead me to the local Joomla setup page. "phpmyadmin" on the other hand does not exist, so the instructions must be off.  What happens when you try to explicitly load [http://localhost/index.php](http://localhost/index.php) in the browser?

---

### Post by Kev261266 on 2012-10-25
when I load [http://localhost/index.php](http://localhost/index.php) I get a 404 Not Found page. The page also states
The requested URL /index.php was not found on this server.
Apache/2.2.22 (Ubuntu) Server at localhost Port 80

I apologise for almost falling back to my windows ways :)

---

### Post by Lars Noodén on 2012-10-25
Ok.  That it's missing still tells us something.  Is your vhost's document root /var/www?   Did you get [Joomla 2.5](http://www.joomla.org/download.html) and untar it in the document root?  Or is it somewhere else?  It needs to be in the vhost's document root. 

Also as part of the set up you will have to configur MySQL, but that can be done when it's needed.

---

### Post by Kev261266 on 2012-10-25
I'm not sure what you mean by "is your vhosts document root /var/www" that is where the index is that displays the "it works....."

Also I've not unzipped (untarred?) a new version of Joomla into there. What I did was move my existing site folders for  myJoomla web sites I'd already built in windows xp, into there.

---

### Post by Kev261266 on 2012-10-25
I think I've made a breakthrough. I downloaded a new version of Joomla and unpacked it into the directory var/www/ now when i go to localhost/index.php it takes me to the installation page (which is what we would expect)

Up until now I've been trying to open sites that I have already built (In Win XP) and not a new installation.

Does this mean that I cannot open any of my existing client sites in ubuntu?

---

### Post by Lars Noodén on 2012-10-25
Ok.  So the real question is not so much about LAMP, most of that seems to be working.  If you are talking about bringing your whole Joomla site over then this is really about [migrating Joomla from Windows to Ubuntu](https://www.google.fi/search?q=migrating+joomla+from+windows+to+linux&aq=f&oq=migrating+joomla+from+windows+to+linux) rather than installation.  

I've not done that at all.  So better advice will come from others.  It does look like you'll also have to move the database contents as well as the PHP files.  If you have mysqldump in Windows that should be useful in extracting the table structure and data to a file and then that can be used to bring it over to Linux.

---

### Post by Lars Noodén on 2012-10-25
> **Kev261266 said:**
> I think I've made a breakthrough. I downloaded a new version of Joomla and unpacked it into the directory var/www/ now when i go to localhost/index.php it takes me to the installation page (which is what we would expect)

Up until now I've been trying to open sites that I have already built (In Win XP) and not a new installation.

Does this mean that I cannot open any of my existing client sites in ubuntu?

Yes, the two sites (Windows and Linux) are separate.  You can start with a fresh install on Linux or try to export the data from mysql in Windows and import it to mysql on Linux. 

If mysqldump is available it might go something like this, but I'm not sure what kind of barriers Windows usage will put in the way:

mysqldump -u root -p Joomla > joomla.sql

---

### Post by Kev261266 on 2012-10-25
Yep, I see what you mean. So the Lamp part seems to be working, am I right in assuming that if I want to create multiple fresh installs I would create folders like this:

var/www/project1
var/www/project2 

and so on?

Also the last thing that I think might be relative to this thread is that in the pre installation check it shows configuration.php writeable - no.

What would I do to make it writeable?

Cheers.

Kev

---

### Post by Lars Noodén on 2012-10-25
Yes, making new subdirectories for the multiple fresh installs will work on the PHP side of things.  I've only looked at Joomla the first time a few minutes ago, so it is not clear if it supports multiple instances on the same database.  You may have to go through the scripts and do a global search and replace of the database name to Joomla2 or something for the second instance.  

About  configuration.php, if you're running the default set up of Apache, it runs as user www-data and group www-data. So you could make the file writeable to the web server like this:

```

sudo chgrp www-data configuration.php 
sudo chmod g=rw configuration.php 

```

I'm always nervous about granting write privileges to the web server.  If something goes wrong, it can be abused badly.

---

### Post by Kev261266 on 2012-10-26
When you say "I'm always nervous about granting write privileges to the web server.  If something goes wrong, it can be abused badly." will this affect the setup I'm trying to achieve? as I don't want to make the virtual server accessible online or on a network, I only want to use it on my machine.

During the installation you guided me through, I do believe that we installed mysql (as part of lamp) 

Now in the past (again Win XP) I would go into phpmyadmin and create a database and password. I would then use this info in the joomla installation. At the moment I don't seem to have phpmyadmin. Would you advise that I install it as in this link here

[http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/](http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/)

Or, is there a ubuntu way to do it that works better?

Thanks again.

---

### Post by mastablasta on 2012-10-26
> **Kev261266 said:**
> When you say "I'm always nervous about granting write privileges to the web server. If something goes wrong, it can be abused badly." will this affect the setup I'm trying to achieve? as I don't want to make the virtual server accessible online or on a network, I only want to use it on my machine.
.
 
he means if it is open to the web. if you only use it for developing&testing behind a router/firewall (i.e. you don't open it to web) then it's ok.
 
 
> 
Now in the past (again Win XP) I would go into phpmyadmin and create a database and password. I would then use this info in the joomla installation. At the moment I don't seem to have phpmyadmin. Would you advise that I install it as in this link here
 
[http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/](http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/)
 

phpmyadmin is graphical tool for mysql. i think it is in software center/repositories. i used it here as well since with a good GUI i don't really need to read a lot of documentation to use the mysql.
 
> 
Or, is there a ubuntu way to do it that works better?

 
you can do it via terminal but as i wrote above it is simpler (to me) to just use phpmyadmin.

---

### Post by Lars Noodén on 2012-10-26
Yes, MySQL was installed as part of the LAMP installation.  The next steps are for either a fresh install of Joomla or a migration from another instance of Joomla are to create the Joomla database.  

phpmyadmin is available in the repositories, so whenever there is a choice to get something from the repository, it is best to take it.  So if there is a Linux or Ubuntu way, that would be it. It saves a lot of work in the long run to let the package manager take care of what is installed and whether it is up to date. 

The instructions that came with Joomla 2.5 also mention using the terminal to create the database and its tables.  One advantage there is that all the actions are clear and unambiguous.  But if you are already familiar with phpmyadmin, go with that because this is about getting the machine set up the way you like it.

---

### Post by Lars Noodén on 2012-10-26
Looking at phpmyadmin, I see that it needs an encrypted connection (HTTPS) to be secure since it is dealing with MySQL users and passwords.  It should have the regular connection (HTTP) disabled.  If that is too much of a side track at this point, then a workaround is to only access it via the localhost and disable remote access in the web server's virtual host configuration:

```

<Location /phpmyadmin/>
        Order deny,allow
        Deny  from all
        Allow from localhost
</Location>

```

---

### Post by Kev261266 on 2012-10-26
I installed phpmyadmin from ubuntu software centre (is that what you mean when you say repositories?) so now that I have that installed I need to run terminal with the following code

```
<Location /phpmyadmin/>         Order deny,allow         Deny  from all         Allow from localhost </Location>
```

do I use the actual word "Location" or is that an actual path i need to get and insert?

---

### Post by Kev261266 on 2012-10-26
I've come across a few snags gents:

1. I tried to run terminal commands to make configuration.php writeable (as per Lars code) and I got 

chgrp: cannot access 'configuration.php' : No such file or directory

So I don't quite know what to do there?

2. I opened phpmyadmin which opened fine and asked me for login details, I entered my ubuntu user name and password but I get

#1045 Cannot log in to the MySQL server

When I ran the setup i didn't enter a password, but I also noted in the user comments when I  installed it that someone had posted "i have treid many and found this as the bestest please make a change by default allow without password"

So do I need to make a login without password change somewhere?

---

### Post by Lars Noodén on 2012-10-26
chgrp and co need to be run from the same directory that configuration.php is in.  Use [cd](http://manpages.ubuntu.com/manpages/precise/en/man1/cd.1posix.html) and [ls](http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1.html) to find your way around.

MySQL has a separate set of users that have nothing to do with the users in Ubuntu.  It's about users in the database itself.  Odds are when you installed LAMP, the MySQL portion of the installation asked you to assign a password to MySQL's root.  Use user 'root' and the corresponding password.  Again, this is a separate system from Ubuntu.

Edit:  Sometimes I have to read two or three times before I understand.  If you missed adding a password for MySQL's root (not Ubuntu's) then you can add it with the following line in the terminal.

```

mysqladmin password

```

---

### Post by Lars Noodén on 2012-10-26
> **Kev261266 said:**
> I installed phpmyadmin from ubuntu software centre (is that what you mean when you say repositories?) so now that I have that installed I need to run terminal with the following code

```
<Location /phpmyadmin/>
         Order deny,allow
         Deny  from all
         Allow from localhost 
</Location>
```

do I use the actual word "Location" or is that an actual path i need to get and insert?
Yes, the software center uses the repositories and it is best to use it whenever you can.  It will make upgrades and security updates easy.

Yes again.  [Location](http://httpd.apache.org/docs/2.2/mod/core.html#location) is a real run-time configuration directive.  The alternate would be [Directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory), but that would require you to set an absolute path.  Location works relative to what the server will give the public.

---

### Post by Kev261266 on 2012-10-26
It's starting to make a bit more sense to me now, but, I tried to add a password for MySQL it let me enter and confirm the password but then gave me this:

mysqladmin: can't turn off logging error: 'Access denied; you need (at least one of) the SUPER privilege(s) for this operation'

---

### Post by Lars Noodén on 2012-10-26
> **Kev261266 said:**
> It's starting to make a bit more sense to me now, but, I tried to add a password for MySQL it let me enter and confirm the password but then gave me this:

mysqladmin: can't turn off logging error: 'Access denied; you need (at least one of) the SUPER privilege(s) for this operation'


Ok.  Try using it with sudo.  It needed to run as (Ubuntu's) root.  And just for good measure, we'll be explicit about MySQL's root.

```

sudo mysqladmin -p -u root password

```

---

### Post by Kev261266 on 2012-10-26
This time I entered the code, gave a password and got:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

---

### Post by Lars Noodén on 2012-10-26
> **Kev261266 said:**
> This time I entered the code, gave a password and got:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

Right, but if you left the MySQL root password blank initially as you wrote above, 

> When I ran the setup i didn't enter a password, but I also noted in the user comments when I installed it that someone had posted "i have treid many and found this as the bestest please make a change by default allow without password"

just hit enter where it asks for the old password.   Then enter the new password and again to confirm it.  

```

sudo mysqladmin -p -u root password

```

---

### Post by Kev261266 on 2012-10-26
Excellent, that worked. I now have PHPmyadmin access.

---

### Post by Kev261266 on 2012-10-31
Well, I think I've got the whole thing working now and I even managed to move my existing sites and databases from the WinXP installation to the new Ubuntu one.

Thank you both for your help.

Kev.

---

### Post by Kev261266 on 2012-11-02
I do however have a query regarding security settings, which we looked at earlier in this thread. I had a chat on the Joomla forums regarding setting file and folder permissions for when I publish sites live (for some reason in linux I need to change the permissions to allow "akeeba kickstart" which is a joomla file unpacker, to work properly)

I was advised to do the following in Linux to make the site secure when I publish it:

1) recursive chmod 755 for directories in /var/www/mysite
```
find /var/www/mysite -type d -print0 | xargs -0 sudo chmod 755
```2) recursive chmod 644 for files in /var/www/mysite
```
find /var/www/mysite -type f -print0 | xargs -0 sudo chmod 644
```3) change the file ownership and group to Apache web server user and group
```
chown -R www-data:www-data /var/www/mysite
```Reasoning for theses modifications:

step 1 and step 2 - to avoid security issue
step 3 - to ensure Apache web server able to execute the files and read / write without any issue

Would you guys agree that this is correct?

Cheers in advance.

Kev.

---

### Post by Lars Noodén on 2012-11-02
> **Kev261266 said:**
> Would you guys agree that this is correct?



Not for step #3 above.  That accidentally gives write access to the whole document root to the web server.  The default is owned by root, group root.  But you can change it to owner kev261266, just as long as it is not owner or group www-data.  

Steps #1 and #2 above already grant read access to www-data through the settings for Other.

---

### Post by Kev261266 on 2012-11-02
So would I change step 3 to:

```
chown -R kev@ubuntu /var/www/mysite
```

where kev@ubuntu is the name that appears in my terminal.

---

### Post by Lars Noodén on 2012-11-02
Yes, and include the group too because that was also set to www-data.

sudo chown -R kev:kev /var/www

---

### Post by Kev261266 on 2012-11-02
I just noticed that you use /var/www rather than /var/www/mysites

if I use /var/www does it apply the settings to all the mysites subfolders at once rather than doing it as a separate instance /var/www/mysite1 and /var/www/mysite2 etc.

Cheers.

Kev.

---

### Post by Lars Noodén on 2012-11-02
Yes, that's what the [-R](http://manpages.ubuntu.com/manpages/precise/en/man1/chown.1posix.html) stands for.  It will recursively change the ownership, getting all files in all subdirectories.  I used /var/www because that's default and you'll have to adjust it for the actual settings you have for your system.

---

### Post by Kev261266 on 2012-11-08
This still is causing me problems, If I can't get this sorted I think I need to go back to windows cos these file permissions and the way Joomla works on ubuntu is driving me crazy.

I used the following code to change directory permissions:
```
     find /var/www/mysite -type d -print0 | xargs -0 sudo chmod 755
```This seems to work okay.

When I put the following code to change file? permissions:
```
find /var/www/mysite -type f -print0 | xargs -0 sudo chmod 644
```I get an error: 
sudo: unable to execute /bin/chmod: Argument list too long

I've not managed to get to step 3:
```
sudo chown -R kev:kev /var/www
```

Am I doing something fundamentally wrong here??

---

### Post by Lars Noodén on 2012-11-08
It might be the order of xargs vs sudo.  Try either of these two.

```

find /var/www/mysite -type f -print0 | sudo xargs -0 chmod 644

find /var/www/mysite -type f -exec sudo chmod 644 {} \;

```

---

### Post by mastablasta on 2012-11-08
the easiest GUI way i found to change permission is via filezilla (i am sure you could also do it with other file browsers). I have a website hosted on linux server. connect via ftp (for example with filezilla), right click on the folder/directory and click properties. then change permissions and make sure that they go all the way down to last level. then just start install and away it goes....
 
i installed many stuff like that and it's preety fast and easy.

---

### Post by Kev261266 on 2012-11-08
Cool, I tried the second option you gave and I got no errors, but during the installation of Joomla It turned out that a configuration.php file was showing as not writeable. So I ran your code twice again, once for d and once for f but changed the file permissions to 777.

This let me write to configuration.php and I'm assuming that if I change the permissions back before I put the site onto a live server, all should be well.

---

### Post by Lars Noodén on 2012-11-08
> **Kev261266 said:**
> Cool, I tried the second option you gave and I got no errors, but during the installation of Joomla It turned out that a configuration.php file was showing as not writeable. So I ran your code twice again, once for d and once for f but changed the file permissions to 777.

This let me write to configuration.php and I'm assuming that if I change the permissions back before I put the site onto a live server, all should be well.

It would be a good idea to change the ownwership back to 755 for the directories and to 644 for the files.  Otherwise, you have granted write access to everyone, including the web server.  World-writable can end up badly.

If there is one specific file, you can change the permissions for just that one file.  See the example in post [#18](http://ubuntuforums.org/showpost.php?p=12317271&postcount=18)

---

### Post by Kev261266 on 2012-11-08
I've been using Krusader which seems great apart from the fact that it won't let me change file permissions.

---

### Post by Kev261266 on 2012-11-08
Now I've installed a Joomla installation (new installation and some of my other old installation sites) the final (I hope) thing that seems to be stopping my sites running the way they should is that mod rewrite appears not to be enabled in the lamp.

The Joomla instructions say this:
> If it is not enabled and you have access to the file apache/conf/httpd.conf, open that file and check if the line LoadModule rewrite_module modules/mod_rewrite.so is uncommented. If necessary, uncomment the line and restart the Apache web server.

But I don't seem to have that file in etc/apache2

is it somewhere else or has it got a different name?

---

### Post by Lars Noodén on 2012-11-08
In Apache2 modules are added or started with a script, [a2enmod](http://manpages.ubuntu.com/manpages/precise/en/man8/a2enmod.8.html).  They are disabled or stopped with another script, [a2dismod](http://manpages.ubuntu.com/manpages/precise/en/man8/a2dismod.8.html).

```

sudo a2enmod rewrite
sudo service apache2 restart

```

If you leave a2enmod blank, it will come up with the full list of available modules.

A lot of the material on the net is very out of date and tells you to edit httpd.conf or some other configuration file. That was how Apache 1.3 did it, but is no longer relevant for Apache2.

---

### Post by Kev261266 on 2012-11-08
I got that done too, but am still having this rewrite problem.

basically Joomla has an option in the backend "Use url rewriting" this would make

[http://localhost/cpc_leds/index.php/what-we-do](http://localhost/cpc_leds/index.php/what-we-do)

look like

[http://localhost/cpc_leds/what-we-do](http://localhost/cpc_leds/what-we-do)

but instead of removing the index.php it displays an error:

not found The requested URL /cpc_leds/what-we-do/ was not found on this server.
  Apache/2.2.22 (Ubuntu) Server at localhost Port 80

Most baffling..

---

### Post by Kev261266 on 2012-11-08
could this be something to do with the file etc/apache2/sites-available/default and the three [AllowOverride None] notations 

I read that these should be changed to AllowOverride All

I know this link refers to a drupal site, but it seems to be the same error that I'm experiencing.

[http://salinaitmind.blogspot.co.uk/2012/05/drupal-clean-url-error-after-migrate-to.html](http://salinaitmind.blogspot.co.uk/2012/05/drupal-clean-url-error-after-migrate-to.html)

and I'm clutching at straws now. :(

---

### Post by Lars Noodén on 2012-11-08
AllowOverride is only useful if you are using .htaccess files, but you don't need them because you yourself have direct access to the web server's configuration file.  

rewrite is probably Apache's most powerful module, but my rewrite experience is *very* rusty.  It might be good to start a fresh thread with an appropriate topic about Apache's mod_rewrite to get more eyes on the problem.

Edit:  Sorry, it's not clear.  Are you using mod_rewrite or is there some special scripting going on in Joomla to try to produce the same effect?

---

### Post by Kev261266 on 2012-11-09
I did enable mod_rewrite as you advised.

But also, Joomla does have a protocol where you need to change a file htaccess.txt to .htaccess in order to make the clean url's work.

I've attached a screenshot to show what I mean. (the first image shows the seo options and the second image shows the info given for the "use url rewriting"

---

### Post by mastablasta on 2012-11-09
> **Kev261266 said:**
> But also, Joomla does have a protocol where you need to change a file htaccess.txt to .htaccess in order to make the clean url's work.

 
then hcnage it. or am i missing something?
 
htaccess are usually found on hosting services.

---

### Post by Kev261266 on 2012-11-09
Whats hcnage? is it a command or  a typo?

Also, I did change it from htaccess.txt to .htaccess but I still get the broken links.

---

### Post by mastablasta on 2012-11-09
typo --> change
 
hmm strange. then again i have it (Joomla) on main site. i installed opencart as subsite but didn't get any broken links.

---

### Post by Lars Noodén on 2012-11-09
> **Kev261266 said:**
> I did enable mod_rewrite as you advised.

But also, Joomla does have a protocol where you need to change a file htaccess.txt to .htaccess in order to make the clean url's work.

I've attached a screenshot to show what I mean. (the first image shows the seo options and the second image shows the info given for the "use url rewriting"

Something is strange. .htaccess should not be needed since you are able to make changes yourself directly in the web server's configuration.  .htaccess is a workarond to grant a small subset of capabilities to an account which does not have the ability to edit the web server's configuration.

But since it is there, what is the content?

---

### Post by Kev261266 on 2012-11-09
I was under the impression that the .htaccess file is there for when the site is uploaded onto a live server. Normally in the past I've done the following:

1. Install a Joomla installation on my localhost
2. Create the site on localhost
3. Compress the site and upload it to my live servers
4. Job done

changing the htaccess.txt to .htaccess in winxp has never caused any problems before.

The .htaccess file of fresh install of joomla onto Ubuntu os is below:

```
##
# @package        Joomla
# @copyright    Copyright (C) 2005 - 2012 Open Source Matters. All rights reserved.
# @license        GNU General Public License version 2 or later; see LICENSE.txt
##

##
# READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE!
#
# The line just below this section: 'Options +FollowSymLinks' may cause problems
# with some server configurations.  It is required for use of mod_rewrite, but may already
# be set by your server administrator in a way that dissallows changing it in
# your .htaccess file.  If using it causes your server to error out, comment it out (add # to
# beginning of line), reload your site in your browser and test your sef url's.  If they work,
# it has been set by your server administrator and you do not need it set here.
##

## Can be commented out if causes errors, see notes above.
Options +FollowSymLinks

## Mod_rewrite in use.

RewriteEngine On

## Begin - Rewrite rules to block out some common exploits.
# If you experience problems on your site block out the operations listed below
# This attempts to block the most common type of exploit `attempts` to Joomla!
#
# Block out any script trying to base64_encode data within the URL.
RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
# Block out any script that includes a <script> tag in URL.
RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
# Block out any script trying to set a PHP GLOBALS variable via URL.
RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
# Block out any script trying to modify a _REQUEST variable via URL.
RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
# Return 403 Forbidden header and show the content of the root homepage
RewriteRule .* index.php [F]
#
## End - Rewrite rules to block out some common exploits.

## Begin - Custom redirects
#
# If you need to redirect some pages, or set a canonical non-www to
# www redirect (or vice versa), place that code here. Ensure those
# redirects use the correct RewriteRule syntax and the [R=301,L] flags.
#
## End - Custom redirects

##
# Uncomment following line if your webserver's URL
# is not directly related to physical file paths.
# Update Your Joomla! Directory (just / for root).
##

RewriteBase /

## Begin - Joomla! core SEF Section.
#
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
#
# If the requested path and file is not /index.php and the request
# has not already been internally rewritten to the index.php script
RewriteCond %{REQUEST_URI} !^/index\.php
# and the request is for something within the component folder,
# or for the site root, or for an extensionless URL, or the
# requested URL ends with one of the listed extensions
RewriteCond %{REQUEST_URI} /component/|(/[^.]*|\.(php|html?|feed|pdf|vcf|raw))$ [NC]
# and the requested path and file doesn't directly match a physical file
RewriteCond %{REQUEST_FILENAME} !-f
# and the requested path and file doesn't directly match a physical folder
RewriteCond %{REQUEST_FILENAME} !-d
# internally rewrite the request to the index.php script
RewriteRule .* index.php [L]
#
## End - Joomla! core SEF Section.

```

---

### Post by mastablasta on 2012-11-09
hmmm i instaleld the 3.0 version. should have checked which one you used. And the issue here is it can't write the configuration, right?

as i only got:
Error
Could not save data. Error: Could not write to the configuration file

and to solve this one the file group of configuration.php file should be www-data

and the group should have read and write access to it. don't know how this is done with command line. or if there is a different way to do this (eg use different group.

edit: i am unsure if in local work htaccess is necessary (as Lars already mentioned).

---

### Post by Lars Noodén on 2012-11-09
> **mastablasta said:**
> ...and to solve this one the file group of configuration.php file should be www-data

and the group should have read and write access to it. don't know how this is done with command line. or if there is a different way to do this (eg use different group...

That is back in #18 above.  

You could use a different group if the web server is a member of another group, but www-data is the default on Ubuntu.

---

### Post by Kev261266 on 2012-11-10
I see what you mean about the .htaccess file, so I did a fresh Joomla install and didn't mess with the rename htaccess.txt to .htaccess.

But I still get the same error as before when I activate the use url re write option in the global config.

I'm currently using Joomla 2.5.8 (3.0 has just recently been released and it's not ready for production use, just yet)

---

### Post by Lars Noodén on 2012-11-10
Can you paste the error as shown in the error log?

---

### Post by Kev261266 on 2012-11-10
where would I find that? 

Or do you mean the error that displays in the browser?

---

### Post by Lars Noodén on 2012-11-10
The default is /var/log/apache2/error.log You can open up a terminal and run this along side the browser window:

```

tail -f /var/log/apache2/error.log 

```

---

### Post by Kev261266 on 2012-11-10
Okay, when I ru the code you gave me, I get:

```
[Sat Nov 10 09:03:03 2012] [error] [client 127.0.0.1] PHP Warning:  file_put_contents(/var/www/cpc/configuration.php): failed to open stream: Permission denied in /var/www/cpc/libraries/joomla/filesystem/file.php on line 418, referer: http://localhost/cpc/administrator/index.php?option=com_config
[Sat Nov 10 10:19:43 2012] [error] [client 127.0.0.1] File does not exist: /var/www/designergie/administrator
[Sat Nov 10 10:21:49 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:49 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:51 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:51 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:23:11 2012] [error] [client 127.0.0.1] File does not exist: /var/www/cpc/test1, referer: http://localhost/cpc/

```

This was generated from a brand new install I've just done.

---

### Post by Spicywoo on 2012-11-11
[QUOTE=Kev261266;12317005]I did that code too but still nothing. I do however think I've spotted an issue.

I had another look at this Joomla doc
[http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop](http://docs.joomla.org/Configuring_a_LAMPP_server_for_PHP_development/Linux_desktop)

and did "1st test for php server" by creating a test file

```
echo "<?php phpinfo(); ?>" | sudo tee /var/www/test.php
```This worked fine and displayed the info as expected. However, when I tried the next step "1st test for phpmyadmin"

by entering localhost/phpmyadmin I get a 404 not found error. The Joomla doc advises me to uninstall lamp and start again from scratch.

Hello Lars & Nooden. I'm at the same point, so I've followed the procedure indicated in this thread. I'm now at the Directory stage, i.e. the 'default' directory, or should I say directories, since there is also a 'default-ssl' script in the /etc/apache2/sites-available folder. Before going any further, I would like to add the 'DirectoryIndex' you indicated. But where exactly and what do I write?

:(

---

### Post by Lars Noodén on 2012-11-11
You can get the whole list of directives here:
[http://httpd.apache.org/docs/2.2/mod/quickreference.html](http://httpd.apache.org/docs/2.2/mod/quickreference.html)

[DirectoryIndex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex) goes in between some <Directory></Directory> directives.

Best to start a new thread if you are starting a new question.

---

### Post by Kev261266 on 2012-11-12
I did read the section where Joomla advises to scrap the whole thin and start with a frexh install of lamp. However, I thought that as we were using linux now, that starting from fresh is counterproductive?

---

### Post by Lars Noodén on 2012-11-12
If you have PHP working then I would disregard advice to reinstall the whole system. You're having a problem with the mod_rewrite rules?  If so, I would start a new thread focusing on the problem with Apache's rewrite rules.

---

### Post by Kev261266 on 2012-11-12
@spicywoo, I seem to remember this happening too, you need to install phpmyadmin from the software centre. As this is a separate gui that uses a browser to connect to php. if you don't install it, you will have to use a terminal to set up your databases etc. Info on this is in this thread.

---

### Post by mastablasta on 2012-11-12
as i need to redo one of our websites i will try to do the 2.5 version of Joomla as well. i only did a test site with 3.0. it seems 3.0 came out not so long ago. plenty new features, new interface, but less plugins than 2.5. however some stuff that needed plugins to work propperly in 2.5 is now buit in 3.0. 
 
i know one thing - i need to keep current URL's

---

### Post by Kev261266 on 2012-11-12
Don't use Joomla 3 yet, it's only released for development purposes and is not recommended for production sites. I've got three new sites to build and I'll be using 2.5.8. There are still way too many background issues with J3.

Well I'll build the sites if I ever get this linux working ;) lets hope I still have some clients left, after messing around trying to get this to work for almost a fortnight.

---

### Post by Kev261266 on 2012-11-12
Joomla provide a Forum Post assistant which displays the system settings. I ran this and I do seem to have quite a few Apache extensions and modules missing (see attached), could this be the cause of the problem?

---

### Post by pkadeel on 2012-11-12
> **Kev261266 said:**
> Okay, when I ru the code you gave me, I get:

```
[COLOR=Red][Sat Nov 10 09:03:03 2012] [error] [client 127.0.0.1] PHP Warning:  file_put_contents(/var/www/cpc/configuration.php): failed to open stream: Permission denied in /var/www/cpc/libraries/joomla/filesystem/file.php on line 418, referer: http://localhost/cpc/administrator/index.php?option=com_config
[Sat Nov 10 10:19:43 2012] [error] [client 127.0.0.1] File does not exist: /var/www/designergie/administrator[/COLOR]
[Sat Nov 10 10:21:49 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:49 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:50 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:51 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:21:51 2012] [error] [client 127.0.0.1] PHP Warning:  Creating default object from empty value in /var/www/cpc/libraries/joomla/updater/adapters/collection.php(101) : eval()'d code on line 1, referer: http://localhost/cpc/administrator/index.php
[Sat Nov 10 10:23:11 2012] [error] [client 127.0.0.1] File does not exist: /var/www/cpc/test1, referer: http://localhost/cpc/

```This was generated from a brand new install I've just done.
What I see is that you are simply having a permission denied error. Your "cpc" folder needs chmod 0777

---

### Post by Kev261266 on 2012-11-12
I tried that too and still get an error.

---

### Post by Kev261266 on 2012-11-12
I've just realised that the image I posted has been shrunk to an unreadable size on here.

So the  potential missing php extensions listed are curl and suhosin

and the potential missing Apache modules are mod_expires mod_security mod_evasive mod_dosevasive mod_ssl mod_qos mod_userdir

I also noticed that even though as a test I set (or thought I set) all the folders and directories to 777 in the section core folders permissions checks, it lists everything as not writeable.

---

### Post by pkadeel on 2012-11-12
> **Kev261266 said:**
> I've just realised that the image I posted has been shrunk to an unreadable size on here.

So the  potential missing php extensions listed are curl and suhosin

and the potential missing Apache modules are mod_expires mod_security mod_evasive mod_dosevasive mod_ssl mod_qos mod_userdir

I also noticed that even though as a test I set (or thought I set) all the folders and directories to 777 in the section core folders permissions checks, it lists everything as not writeable.
you can install the missing extenssions and modules
```

sudo apt-get install php5-curl php5-suhosin
sudo apt-get install libapache2-mod-qos libapache2-modsecurity libapache2-mod-evasive 
sudo a2enmod expires
sudo a2enmod ssl
sudo a2enmod userdir

```For rest of the 3 newly installed modules, look for their module names in the mod-available folder and use sudo a2enmod module-name to enable it.

However I have never seen a permission denied error arising due to any missing module or php extenssion. Read the joomla documentation and carefully examine all the permission requirements not only folders but also for files. There might be some files requiring elevated permissions to operate properly.

---

### Post by mastablasta on 2012-11-15
perhaps the wrong user has that permission. i think you need ot make sure that apache server has permission
 
as a side note i decided not to test 2.5 (well i might sitll try it again) but instead i will go with version 3. because version 3 is mobile friendly and if you think ahead that's what it will be needed in the near future. page that is nicely rendered on tablets and phones as well as on PC.
 
i would like to send you my configuraitons but i do not know how to pull out the data. i will check permissions and let you know how i set it up. i have it set up in virtualbox as a test system so to me it's no problme if others see it since i have no personal data there.

---


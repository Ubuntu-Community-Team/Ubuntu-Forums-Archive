---
title: "Browser cannot run php script"
date: 2012-08-09
forum: Programming Talk
---

### Post by sid0972 on 2012-08-09
i installed the whole LAMP stack in ubuntu, following these instructions

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

using terminal, i can run the script

but in browser, i cannot, it just downloads the file, and opens it in text editor
how can i see the output in browser?

---

### Post by lisati on 2012-08-09
The page you linked to has a suggestion for this problem: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

---

### Post by dazman19 on 2012-08-09
well you have to set up apache to pre-process php files by the Hypertext Preprocessor.

Editing the /etc/apache2/apache2.conf file should have a like like this:

AddType application/x-httpd-php .php .php5

if not add it.


then sudo a2enmod php5

then sudo /etc/init.d/apache2 restart

---

### Post by sid0972 on 2012-08-09
> **lisati said:**
> The page you linked to has a suggestion for this problem: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)


no, that says module is missing, but it exists


> **dazman19 said:**
> well you have to set up apache to pre-process php files by the Hypertext Preprocessor.

Editing the /etc/apache2/apache2.conf file should have a like like this:

AddType application/x-httpd-php .php .php5

if not add it.


then sudo a2enmod php5

then sudo /etc/init.d/apache2 restart

i checked for that line, wasnt there, tried to add it, says i cant save it cause i dont have permissions

EDIT
found gksudo, added the comment and saved it, same problem
what else can i do now?
reinstall LAMP server?

Tried [this]("http://ubuntuforums.org/showthread.php?t=1466591&highlight=php+problem") thread as well, no luck

---

### Post by sid0972 on 2012-08-09
i just checked, my httpd.conf file is empty

is that normal?

i can run phpinfo, it displays everything in the terminal
every script runs absolutely fine in terminal, but not in browser

b the way sudo a2emod php5 shows module is already enabled

---

### Post by dazman19 on 2012-08-09
Yep httpd.conf file being empty is perfectly normal for ubuntu/debain. Dont know why. But you use the /etc/apache2/apache2.conf instead. 

You need to make sure the mime type directive is there. If not add it. Ensure php is enabled in apache using a2enmod. (a2 enable module)

if you run phpinfo in the terminal by having a file like this 

phpinfo.php
[PHP]
<?php 
phpinfo();
?>
[/PHP]

```

$ php phpinfo.php  

```

Look for Loaded Modules. 

These will tell you what is enabled. Here is mine:

core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env mod_mime mod_negotiation mod_perl mod_php5 mod_python mod_reqtimeout mod_rewrite mod_setenvif mod_status 

you probably dont need all of these because i do a lot of open ssl work. But you need mod_php5 enabled in apache.

Since you can run php from the terminal but not from apache its probably either 1 of two things.
1) you dont have the apache module enabed. 
to enable do 
```
sudo a2enmod php5
```
Then restart apache2

2) you have no mime type directive for the web server, so it doesnt know what to do with php files.

do this from terminal:

```
sudo nano /etc/apache2/apache2.conf
```

Add this line: 

```
AddType application/x-httpd-php .php .php5
```

Then save ctrl + x and press y to save. and then restart apache2.

```
sudo /etc/init.d/apache2 restart
```

If you have done both of these steps and restarted apache2 and it is still not working. Then you will probably need to show us your /etc/apache2/apache2.conf file. DO NOT WORRY ABOUT httpd.conf this is essentially your apache2.conf file.

---

### Post by sid0972 on 2012-08-09
i restarted the apache server and i got this error

Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

i looked it up [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Apache"), restarted apache again 
error is gone but the problem persists

and as for the addType line, i added it already
i just put it there randomly (and not commented it of course)

do i have to put it at a specific position?

when [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_Apache") link says i have to add servername localhost, do i have to type this exactly or do i have to type something else, like 127.0.0.1 in place of localhost?
tried that too but didnt work

---

### Post by spjackson on 2012-08-09
This is all very puzzling.

I haven't installed LAMP on Ubuntu very often, maybe half a dozen times, but on all those occasions that I have, I haven't had to go tinkering with config files for the basic installation which just works out of the box. In particular, if the right packages are installed, php just works without tweaking.

The fact that this isn't working for you suggests to me that something has gone wrong with the package installation. Maybe I've just been lucky, but I don't think so.

If I were you, I would uninstall the LAMP stuff and start again. However, you can try to fix it if that's what you prefer.

I have 2 Ubuntu systems with LAMP currently available, one on 10.04 and one on 12.04. Neither of these has 
```

AddType application/x-httpd-php .php .php5

```in /etc/apache2.conf.

Here are all the references to php in /etc/apache2/... that the LAMP install creates on Ubuntu 12.04. This is a system where php is working as expected through the browser - no tweaking or customisation.
```

$ find /etc/apache2 -type f -exec fgrep -i php {} /dev/null \;
/etc/apache2/sites-available/default-ssl:    <FilesMatch "\.(cgi|shtml|phtml|php)$">
/etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-available/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/mods-available/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-available/php5.conf:    SetHandler application/x-httpd-php
/etc/apache2/mods-available/php5.conf:    <FilesMatch "\.phps$">
/etc/apache2/mods-available/php5.conf:    SetHandler application/x-httpd-php-source
/etc/apache2/mods-available/php5.conf:    # To re-enable php in user directories comment the following lines
/etc/apache2/mods-available/php5.conf:            php_admin_value engine Off

```

---

### Post by sid0972 on 2012-08-10
after running the command you gave above, here is my output

> /etc/apache2/httpd.conf~:AddType application/x-httpd-php .php .php5
/etc/apache2/mods-available/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-available/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-available/php5.conf:	SetHandler application/x-httpd-php
/etc/apache2/mods-available/php5.conf:    <FilesMatch "\.phps$">
/etc/apache2/mods-available/php5.conf:	SetHandler application/x-httpd-php-source
/etc/apache2/mods-available/php5.conf:    # To re-enable php in user directories comment the following lines
/etc/apache2/mods-available/php5.conf:            php_admin_value engine Off
/etc/apache2/apache2.conf:AddType application/x-httpd-php .php .php5
/etc/apache2/mods-enabled/php5.conf~:<IfModule mod_php5.c>
/etc/apache2/mods-enabled/php5.conf~:	SetHandler application/x-httpd-php
/etc/apache2/mods-enabled/php5.conf~:    <FilesMatch "\.phps$">
/etc/apache2/mods-enabled/php5.conf~:	SetHandler application/x-httpd-php-source
/etc/apache2/mods-enabled/php5.conf~:    # To re-enable php in user directories comment the following lines
/etc/apache2/mods-enabled/php5.conf~:            php_admin_value engine Off
/etc/apache2/apache2.conf~:AddType application/x-httpd-php .php .php5
/etc/apache2/sites-available/default-ssl:	<FilesMatch "\.(cgi|shtml|phtml|php)$">


---

### Post by sid0972 on 2012-08-11
SO, i finally got it working, but partially

i re-installed lamp server, and i am able to run php scripts
but i have to set the permissions of the folder to read and write files for everyone, which is set in var/www
when i type the full address of the file in browser, they are executed
but if i try to open the file, open with firefox, it prompts to be downloaded
but when i open them from other folder, local disk/myFolder for example, then they wont even run, even if i type the full address of the file in the browser
i think it is permissions issue

how can i change it?

when i try to change it, it automatically sets back to none (--)

gksudo chmod 777 didnt help

---

### Post by spjackson on 2012-08-11
> **sid0972 said:**
> SO, i finally got it working, but partially

i re-installed lamp server, and i am able to run php scripts

Good, so it should.
> 
but i have to set the permissions of the folder to read and write files for everyone, which is set in var/www
In order for apache to be able to read & execute a php script, the user that runs apache needs read permission on the file, plus execute permission on the directories in the path to the file. The user that runs apache is normally www-data.

So for example, for [http://localhost/myscript.php](http://localhost/myscript.php) to work, assuming DocumentRoot to be /var/www, then user www-data needs execute permission on /, /var, /var/www and read permission on /var/www/myscript.php.

> 
when i type the full address of the file in browser, they are executed
but if i try to open the file, open with firefox, it prompts to be downloaded
Do you mean by going through the Firefox menu, File->Open File? That bypasses apache. Firefox does not have the capability to run the script like this (maybe there's a plugin, I don't know).
> 
but when i open them from other folder, local disk/myFolder for example, then they wont even run, even if i type the full address of the file in the browser
i think it is permissions issue
Ditto. Apache will in general run the script if you are using [http://.](http://.).. or [https://.](https://.).. . Other methods of file access, including file:///... in Firefox will not run it.

Note also that say [http://localhost/~someuser/myscript.php]("http://localhost/%7Esomeuser/myscript.php") will normally display the script, not run it. This is because with the default install, running scripts in ~someuser/public_html/ is disabled. You need to edit /etc/apache2/mods-available/php5.conf if you want to change this. There is a comment that explains what to do.

> 
how can i change it?

when i try to change it, it automatically sets back to none (--)

gksudo chmod 777 didnt helpWhat sort of filesystem is the file on?

---

### Post by sid0972 on 2012-08-11
> **spjackson said:**
> 
Do you mean by going through the Firefox menu, File->Open File? That bypasses apache. Firefox does not have the capability to run the script like this (maybe there's a plugin, I don't know).
Ditto. Apache will in general run the script if you are using [http://.](http://.).. or [https://.](https://.).. . Other methods of file access, including file:///... in Firefox will not run it.


no, by typing the full address in the browser, like file:///~drives//a.php
> 

What sort of filesystem is the file on?

ext4


i found gksudo nautilus, will try and report back

---

### Post by spjackson on 2012-08-11
> **sid0972 said:**
> no, by typing the full address in the browser, like file:///~drives//a.php

Well, as I said, this bypasses apache. Firefox does not run php scripts for you, unless there's a plugin that will do it.

---

### Post by sid0972 on 2012-08-11
then how does it get executed if it is bypassed?

---

### Post by SeijiSensei on 2012-08-11
Make sure you have the **libapache2-mod-php5** package installed.

---

### Post by sid0972 on 2012-08-11
it is, i checked

---

### Post by spjackson on 2012-08-11
> **sid0972 said:**
> then how does it get executed if it is bypassed?
It doesn't. I thought you were saying that the problem was that it doesn't get executed. If you want your script to be executed, then you need to use apache and you do that by using [http://.](http://.).. (or [https://.](https://.)..).

If you use file:///var/www/index.html Firefox does not use apache, it opens the file in the local filesystem, using your own access permissions, not those of www-data, and Firefox does not run php for you.

You could stop or uninstall apache and you would still be able to access files via e.g. file:///var/www/index.html (assuming you have permission).

---

### Post by sid0972 on 2012-08-12
turns out you are right
also the documentation says the same thing,. if it is being opened as file:///, it is not being parsed

i tried installation in fedora, windows 7, peppermint os, all have the same problem
and i have tried so many different configs for so many different OS, i am TOTALLY confused

till the time i figure it out, can anyone please tell me which distribution comes with php, apache and mysql pre-installed and pre-confiured?

---

### Post by trent.josephsen on 2012-08-12
You said "all have the same problem" -- what problem? You understand why Apache wasn't running the script, right? Or are you having another issue?

---

### Post by sid0972 on 2012-08-12
yeah the one you referred to, why Apache cannot parse the scripts, in any of the OS

---

### Post by trent.josephsen on 2012-08-12
Not interpreting a script that was accessed via a file:// URL is not a problem, nor a bug nor a feature; it's just how things work.

Apache is an HTTP server. It only handles HTTP requests that come in on TCP port 80 (or whatever port you configure it to listen on) from a connected client.

When you type file:///path/to/file in the address bar, the browser doesn't create an HTTP request or connect to any port on any machine; it looks for /path/to/file in the same way any other program does it, like an editor or a file manager. Just as if you had typed `cat /path/to/file` in a terminal. Apache doesn't have anything to do with it. The kernel won't summon Apache to interpret an arbitrary file just because it looks like PHP code; if it did, you couldn't edit it to begin with.

You need to use an http:// (or https) URL to cause your browser to create an HTTP request and connect to the Apache server.

---

### Post by utnubuuser on 2012-08-12
If this is a development server on your own machine:

sudo chown /var/www yourusername

then: 

sudo /etc/init.d/apache2 restart

---

### Post by spjackson on 2012-08-12
> **sid0972 said:**
> turns out you are right
also the documentation says the same thing,. if it is being opened as file:///, it is not being parsed

i tried installation in fedora, windows 7, peppermint os, all have the same problem
and i have tried so many different configs for so many different OS, i am TOTALLY confused

till the time i figure it out, can anyone please tell me which distribution comes with php, apache and mysql pre-installed and pre-confiured?
Your Lamp installation on Ubuntu does the job perfectly, provided you are prepared to use Apache. If you refuse to use Apache by refusing to use http, then no amount of configuring Apache, reinstalling it or restarting it, will do you one ounce of good.

I suggest you follow the pattern of the vast majority of web developers and test using [http://localhost/myscript.php](http://localhost/myscript.php) and your "problem" is solved, as you wrote yesterday.
> 
SO, i finally got it working, but partially

i re-installed lamp server, and i am able to run php scripts
but i have to set the permissions of the folder to read and write files for everyone, which is set in var/www
when i type the full address of the file in browser, they are executed
If you are looking for a platform that will process file:/// in a web browser just as though it had gone through a webserver, then I don't believe you will find one.

---

### Post by sid0972 on 2012-08-13
> **spjackson said:**
> Your Lamp installation on Ubuntu does the job perfectly, provided you are prepared to use Apache. If you refuse to use Apache by refusing to use http, then no amount of configuring Apache, reinstalling it or restarting it, will do you one ounce of good.

I suggest you follow the pattern of the vast majority of web developers and test using [http://localhost/myscript.php](http://localhost/myscript.php) and your "problem" is solved, as you wrote yesterday.
If you are looking for a platform that will process file:/// in a web browser just as though it had gone through a webserver, then I don't believe you will find one.

no mate, i have no intention of running them as file:///
its just that i didnt know that while accessing scripts as file:/// will not call apache, until you kindly told me.
 
also, even if i try http:// method, it shows "it works" page
but when i open file info.php, which has [PHP]phpinfo();[/PHP] in it, it just wont run, it asks to be downloaded

not just this, any script wont run, just downloads

---

### Post by sid0972 on 2012-08-13
another update, i deleted my apache2 folder
and i cannot install it again
 sudo apt-get install apache2 says i  have the latest version already

do i need to re-install ubuntu?
i tried repairing broken packages, no luck

---

### Post by spjackson on 2012-08-13
> **sid0972 said:**
> 
also, even if i try http:// method, it shows "it works" page
but when i open file info.php, which has [PHP]phpinfo();[/PHP] in it, it just wont run, it asks to be downloaded

not just this, any script wont run, just downloads
So what did you mean when you said this?
> 
when i type the full address of the file in browser, they are executed                      
I'm totally confused about what you are saying the symptoms are now.

---

### Post by sid0972 on 2012-08-13
earlier, before i deleted apache2 folder, following were the cases

1) input- [http://localhost](http://localhost)                  
   output- "it works"

2) input- [http://localhost/info.php](http://localhost/info.php)      
   output- nothing

3) input- file:///~someDirectory/info.php        
   output- file executed

for the time being i have installed XAMPP on my windows
it runs [http://localhost/info.php](http://localhost/info.php) and shows the output

i just have one question
when i right click on a file and open it using browser, it displays the script itself, as it is, including html and php
but when i access it by localhost/filename.php, it is executed successfully, 
is this how it is meant to be?

---

### Post by trent.josephsen on 2012-08-13
> **sid0972 said:**
> 2) input- [http://localhost/info.php](http://localhost/info.php)      
   output- nothing

What does "nothing" mean? A 404 error is not what I would call "nothing". Nor is an HTTP response with no content (0 bytes). Be precise.

> 3) input- file:///~someDirectory/info.php        
   output- file executed
file:///anything should never have executed the file.

> i just have one question
when i right click on a file and open it using browser, it displays the script itself, as it is, including html and php
but when i access it by localhost/filename.php, it is executed successfully, 
is this how it is meant to be?

Yes.

---

### Post by sid0972 on 2012-08-13
by noting i meant browser goes into an endless loop where it would just process the document (the circle keeps revolving at the top) and white screen is constant till i close it

i found out about skype, i have it installed, maybe that is not allowing port 80 and 443 to be accessed
how can i re-install apache2?
i try it, says i have it installed already
but directory /etc/apache2 doesnt exist

---

### Post by trent.josephsen on 2012-08-13
You have borked your apache installation. Fixing it is probably going to be complicated. Maybe it can be a lesson learned?

---

### Post by sid0972 on 2012-08-14
it is, so do i need to re-install ubuntu?

---

### Post by sid0972 on 2012-08-14
XAMPP works fine on ubuntu, so i'll just use that one itself
thank you all for your answers

it was written in the documentation that its not as safe as LAMP, and has many security issues
i am just using it for development and learning, not to actually create a web server, is it fine without that?

---


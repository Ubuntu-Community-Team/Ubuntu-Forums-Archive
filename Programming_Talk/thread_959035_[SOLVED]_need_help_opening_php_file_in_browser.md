---
title: "[SOLVED] need help opening php file in browser"
date: 2008-10-26
forum: Programming Talk
---

### Post by AlexenderReez on 2008-10-26
i cant open php file even after i install php5 and  follow this guide [link1]("http://ubuntuforums.org/showthread.php?t=692720")..i'm following this guide [link2]("http://www.scribd.com/doc/128662/Create-dynamic-sites-with-PHP-MySQL?from_email_04_friend_send=1")

i try to create database that interact with html document using php...i have create in phpMyAdmin as show below.but the main problem is,when i open php file using brower,it start asking for downloading instead of execute it...(as shown below)

any help would be really appreciated..i have search a lot using google.com but unfortunately doesn't seem found any page that can help me...

---

### Post by AlexenderReez on 2008-10-27
i'm waiting


:(

---

### Post by AlexenderReez on 2008-10-27
i can't even open php file in browser .i have try all guide appear in google search but nothing works...my question in the [ubuntuforum]("http://ubuntuforums.org/showthread.php?t=959035") or [html]("http://www.htmlcodetutorial.com/help/sutra44764.html#44764") forum also don't receive any respond.i have install php5.

my  /etc/apache2/httpd.conf

```
# PHP Configuration for Apache
#
# Load the apache module
#
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
#
# Cause the PHP interpreter handle files with a .php extension.
#
<Files *.php>
SetOutputFilter PHP
SetInputFilter PHP
LimitRequestBody 9524288
</Files>
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
#
# Add index.php to the list of files that will be served as directory
# indexes.
#
DirectoryIndex index.php

```
and..
```
[ reez @ alexendeRReez : /home/reez ] sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Tue Oct 28 09:11:32 2008] [warn] module php5_module is already loaded, skipping
[Tue Oct 28 09:11:42 2008] [warn] module php5_module is already loaded, skipping
                                                                         [ OK ]
```
please help..i'm really full of pressure(really pissed me of) just to get php file execute in broswer instead of downloading whatever it is.....

---

### Post by skullmunky on 2008-10-31
try this guide instead:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

I think the first guide you were following only shows you how to run PHP code as executable scripts locally from the terminal, not how to use php with apache. 

The second guide is a little old so isn't the best one to follow for recent ubuntu's.  It uses apache 1.3 and php4, and is all based on compiling everything from source.  In ubuntu you can just install apache, php, mysql, etc. from synaptic so it's a lot less work.  Also note that a lot changed between apache 1.3 and apache 2 with the layout of server configuration files so instructions for 1.3 may not work anymore.  That's probably the trouble you're having.  Anyway, try the ubuntuguide guide, it should be pretty quick and painless.

---

### Post by hessiess on 2008-10-31
try putting the file in /var/www then browse to it, normally [http://localhost](http://localhost)

---

### Post by Reiger on 2008-10-31
Also check the default mime type your PHP generated page is served as: most browsers still want this to be text/html or else they'll try to download it instead.

---


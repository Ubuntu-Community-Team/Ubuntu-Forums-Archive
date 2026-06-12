---
title: "mod_rewrite loaded but not working"
date: 2009-10-21
forum: Programming Talk
---

### Post by showman47 on 2009-10-21
Hi


I'm having a problem getting mod_rewrite to work on my home server.

I've setup linux-server on my home pc and have apache2-php-mysql all working fine and mod-rewrite is definately loaded in apache
(phpinfo shows it enabled, webadmin shows it as enabled and using the command line 
sudo a2enmod rewrite also shows it enabled)

I'm using a test that I found here:
[http://www.wallpaperama.com/forums/how-to-test-check-if-mod-rewrite-is-enabled-t40.html](http://www.wallpaperama.com/forums/how-to-test-check-if-mod-rewrite-is-enabled-t40.html)

which works on my shared hosting, but not on my home server.
the .htaccess file contains:

RewriteEngine On

RewriteRule ^link([^/]*).html$ rewrite.php?link=$1 [L]

and a php script:

<?php

if($_GET['link']==1){echo"You are not using mod_rewrite";}

elseif($_GET['link']==2){echo"Congratulations!! You are using Apache mod_rewrite";}

else{echo"Linux Apache mod_rewrte Test Tutorial";}

?>

This definitely works on my shared hosting, so I'm concluding that I have a problem with my apache2 config.

Another possible clue (I'm still a newbie at configuring apache)
is that when I try and restart apache from the terminal :

sudo service apache2 restart

I get the message: 'Could not not determine the servers fully qualified domain name, using 127.0.1.1 for Servername'

but apache does restart ok and I can use the webserver on [http://localhost](http://localhost) without any problems, except for mod_rewrite

I'm sure it's a apache config problem

Any help appreciated.

Showman

---

### Post by januzi on 2009-10-21
[http://httpd.apache.org/docs/2.1/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.1/mod/core.html#allowoverride)

---

### Post by showman47 on 2009-10-21
Thankyou !

I inserted :
    <Directory "/var/www/test">
        AllowOverride ALL
    </Directory>

into the apache config file and it works a treat

Showman

---

### Post by betweenbrain on 2009-10-27
Thanks for posting your solution. For anyone else looking for this, check out [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

---


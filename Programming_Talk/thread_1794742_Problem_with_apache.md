---
title: "Problem with apache???"
date: 2011-07-01
forum: Programming Talk
---

### Post by scott_tiger on 2011-07-01
I have made some php files and that works well when i run on my desktop (on apache server).

But when I tried the same php files to run on my friends computer's apache server it is showing **FORBIDDEN** **cannot run on this server..**

restarting the server using cmd **sudo /etc/init.d/apache2 restart**   also didnot work..

Please Help???

---

### Post by Dangertux on 2011-07-01
Check the following.

That PHP is correctly installed.  Also make sure that the program you wrote isn't utilizing disabled functions from the php.ini

---

### Post by scott_tiger on 2011-07-02
PHP was installed correctly,no problem with it...

No  disabled function used in php.ini..

---

### Post by SeijiSensei on 2011-07-02
Sounds like a permissions problem to me.  Can the Apache user read the files you copied over?  (Must be readable by user www-data on Ubuntu, or user httpd on RedHat-flavored machines.) In the <VirtualHost> container, iss the DocumentRoot correctly set? Is there a <Directory> stanza for the directory referenced in DocumentRoot?

What do you see in /var/log/apache2/error.log (on Ubuntu) or in /var/log/httpd/error_log (RedHat/CentOS/etc.)?

---


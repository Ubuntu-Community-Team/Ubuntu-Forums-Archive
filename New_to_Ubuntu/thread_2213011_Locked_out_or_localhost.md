---
title: "Locked out or localhost"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by kapi on 2014-03-24
Hope someone can help 

Just tried to access local host and received this error message

Forbidden

You don't have permission to access / on this server.

Apache/2.2.22 (Ubuntu) Server at localhost Port 80

---

### Post by 7sbaV8Kt5PTh on 2014-03-24
Is there a .htaccess file getting in the way?  Can you check /var/log/apache2/error.log for any relevant messages?  Did you recently change the virtual host definition in /etc/apache2/sites-enabled/<your site>?  Did the permissions change on the website directory?  (/var/www/site or wherever it is).

Those are the things to check out; the list is long on what it could be...

---


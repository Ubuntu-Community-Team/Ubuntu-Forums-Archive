---
title: "[SOLVED] Web Server - Where is the root web?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by WebSiteGuru on 2008-06-30
Hi everyone.

I just installed a fresh copy of Ubuntu. And I installed the Apache server / MySQL. I don't know where is the location of the webroot. Can someone point me to the right direction.

Also, how do I create the database for mySQL? Thanks!

---

### Post by cariboo on 2008-06-30
The document root is /var/www. If you look in /etc/apache2/sites-available/defautl you can see the setting there.

Jim

---

### Post by WebSiteGuru on 2008-07-03
Thank you! :D:popcorn:

---


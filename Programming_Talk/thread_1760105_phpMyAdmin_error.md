---
title: "phpMyAdmin error"
date: 2011-05-16
forum: Programming Talk
---

### Post by 15176568 on 2011-05-16
For anybody who can help, I'm currently getting the following error if I try to open phpMyAdmin in Xampp:

**>phpMyAdmin - **

 >Cannot start session without errors, please check errors given in  your PHP and/or >webserver log file and configure your PHP installation  properly.


Before I installed Xampp I had an apache2 server installed from the repositories together with phpMyAdmin. I tried solving the error by installing a fresh copy of Xampp and removing the apache2 as well as phpMyAdmin.
However the same problem persisted.


If I start the lampp server, everything starts fine. No errors or problems is given.



I run ubuntu 11.04. I've never got this error in the past using Xampp.


Does anybody have the same problem or can anybody help?


Thanks.

---

### Post by roccivic on 2011-05-17
The usual fix for this is to clear the cookies in your browser and restart apache:

```
sudo /etc/init.d/apache2 restart
```

If you still have problems, try the PMA forums: [http://sourceforge.net/projects/phpmyadmin/forums](http://sourceforge.net/projects/phpmyadmin/forums)
or come talk to us on #phpmyadmin at irc.freenode.net

---


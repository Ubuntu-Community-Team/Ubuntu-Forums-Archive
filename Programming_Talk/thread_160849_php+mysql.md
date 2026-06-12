---
title: "php+mysql"
date: 2006-04-15
forum: Programming Talk
---

### Post by orlox on 2006-04-15
Hi, im trying to use php4 together with an apache server and mysql. I have them  all installed, together with the php4-mysql package, but when trying to run a php script with mysql instruction, it throws things like

[HTML]
Fatal error: Call to undefined function: mysql_pconnect() in /var/www/hello.php on line 8
[/HTML]

How can I get this to work?

---

### Post by Ensnared on 2006-04-15
If you just installed the package, it may be that you just need to restart the httpd-daemon for it to work. Try it:
```
sudo /etc/init.d/apache2 restart
```
(It may be httpd or apache instead of apache2, I'm on my laptop now so I can't check to make sure :P)

If that fails, try using mysql_connect() instead just to see if that works. You can also create a php-file with only this content, and open it in your browser, to see if mysql-support is actually working properly:```
<?php
phpinfo();
?>
```

---

### Post by orlox on 2006-04-15
Restarting the server was all I need...thanks for your answer

---


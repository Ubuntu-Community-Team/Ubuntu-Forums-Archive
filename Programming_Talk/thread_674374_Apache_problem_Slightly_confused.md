---
title: "Apache problem? Slightly confused"
date: 2008-01-21
forum: Programming Talk
---

### Post by dazulu on 2008-01-21
**[COLOR="Green"][SOLVED] I don't know how but it somehow fixed itself within minutes and is now working like I wanted.[/COLOR]**

Very new to linux yet I managed to get apache2/php5/mysql5/phpmyadmin working and also managed to change the document root from var/www to myfolder/www. Slight problem though...

When I go to my document root through [http://localhost](http://localhost) and click on my test.php with phpinfo();, it gives my all the information so I know my php is working.

Yet when i go to [http://localhost/mywebsite](http://localhost/mywebsite) it doesn't recognise the index.php. however when I go to  127.0.0.1/mywebsite or 127.0.1.1/mywebsite or 127.0.2.4/mywebsite etc. etc., it recognises the index.php and reads from my mysql database no problems...

I'm slightly confused as to what's happening here... I'd like to be able to just go to [http://localhost/mywebsite](http://localhost/mywebsite) and have it working :S

---

### Post by LaRoza on 2008-01-21
Perhaps Apache needed a restart, and you did that without thinking about it.

---


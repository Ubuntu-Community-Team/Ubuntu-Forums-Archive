---
title: "unable to use .asp in ubuntu"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by tikolo on 2012-10-19
Hi There, 

I created a simple .html page which calls .asp page from <href> tag but when I click on that instead of running .asp page, it simply opens the code of .asp page in browser.. :( can some one tell me what I am missing ? I am using 10.4 LS version and I have Apache and php installed. is there anything else I need to install for .asp ? if so what is it and how can do it.

---

### Post by StinkySQL on 2012-10-19
You'll have some wrangling to do to set Apache up for that. It doesn't do it out of the box. I'm not an Apache guy, but this link may be what you are looking for ...

[http://sebastians-pamphlets.com/how-to-migrate-a-website-from-iis-asp-to-apache-php/](http://sebastians-pamphlets.com/how-to-migrate-a-website-from-iis-asp-to-apache-php/)

---

### Post by tikolo on 2012-10-22
I created a sumple .txt file with following content and named it as .htaccess and placed in /var/www/html folder but still same issue.. am I doing some thing wrong ?

AddType text/html .asp
AddHandler application/x-httpd-php .asp

---


---
title: "Problems with php and apache on Ubuntu"
date: 2011-01-11
forum: Programming Talk
---

### Post by johnlocke on 2011-01-11
Hi,
I'm trying to set up a LAMP environment on my Maverick machine
I have installed the following packages:
php5,
php5mysql,
apache2
and libapache2-mod-php5

I have also installed the Eclipse PDT (PHP Dev. Tools) as my IDE.

Going on my browser to [http://localhost](http://localhost) gives me the "It works!" message, and when I run php in terminal on a sample phpinfo file I get all the details.

The problem is, when I run a PHP file in Eclipse I get:

"Not Found

The requested URL /Site/index.php was not found on this server."
And when I open a php file through my browser it treats it as if I want to download it.

Could someone please direct me on how to configure all the needed packages(Including Eclipse configurations)

Thanks alot,
John Locke

---

### Post by edpatterson on 2011-01-11
I too came looking for help getting Eclipse PDT working. I have numerous sites running on my box and wanted to move to Eclipse. I get the same error. Tried looking on the Eclipse site. Your basic case of too much information.

---

### Post by johnlocke on 2011-01-13
Resolved it myself:
It was quite silly actually,
I just had to make sure the directory where all the files you want to publish are found is the same as the eclipse workspace directory

All you have to do is(in terminal):
gedit  /etc/apache2/sites-available/default (change if apache directory is different)
and change the line "DocumentRoot /var/www" to your eclipse workspace directory

Hope it helps!

---


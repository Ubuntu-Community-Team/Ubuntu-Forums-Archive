---
title: "Using PHP in Firefox"
date: 2011-12-10
forum: Programming Talk
---

### Post by Foxes on 2011-12-10
Whenever I try to open my PHP files in Firefox, it wants me to download them. I have read through a lot of the existing topics about this already and found that it requires Apache, which I installed to still have the issue. The only fix that I have found on this board already is to edit the httpd.conf file, but it opens as read only for me and is completely blank. Going to [http://127.0.0.1/](http://127.0.0.1/) (which is a loop back to my computer) gives me a page that says, "It works!" I would like to get to my home/user folder using it, but [http://127.0.0.1/home](http://127.0.0.1/home) gives nothing and neither does [http://127.0.0.1/user](http://127.0.0.1/user). Please tell me what I need. Thank you. :)

---

### Post by Bachstelze on 2011-12-10
You also need to install the PHP module for Apache, it's libapache2-mod-php5.

---

### Post by lisati on 2011-12-10
Some tips for dealing with PHP files that get downloaded instead of displayed can be found here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

---

### Post by Foxes on 2011-12-10
Thank you. It is all installed now but I still do not know how to navigate to my a folder in my home/user directory. Can I get some information on that? Thank you.

---

### Post by Bachstelze on 2011-12-10
Navigating to the home directory of users will require manual configuration, and is generally a bad idea. What you can do is enable the userdir module, and then each user can create a public_html directory in their home directory, and files put there will be accessible at [http://server/~user](http://server/~user).

---

### Post by Foxes on 2011-12-10
Thank you. ;)

It gets to the directory now but clicking on the PHP file I put there still results in it trying to download.

---

### Post by Bachstelze on 2011-12-10
Have you restarted Apache after installing PHP ?

---

### Post by Foxes on 2011-12-10
I used this to restart it:
```
sudo restart apache2
```

---

### Post by dazman19 on 2011-12-11
yep that should have worked.

If it didnt resart you should probably use 

```
sudo /etc/init.d/apache2 restart
```

If it is still not invoking the preprocessor then you should add this to your apache configuration.

AddType application/x-httpd-php .php

This can be done at multiple levels. Usually your httpd.conf file or your apache2.conf depending on your configuration.

You can try adding it to the vhosts file under /etc/apache2/sites-available/(name of vhost file) 

remember if you add something to the vhosts file under sites-available you will need to enable the site then restart the server. 

```
a2ensite sitename
```

then run the apache restart command i told you about above.

Failing that, you may need to re-compile apache2 or php as you will be missing something. Usually after a fresh ubuntu install you can get away with

sudo apt-get install mysql-server php5 apache2 php-mysql .....
(where the ... is any other extensions you need).

---


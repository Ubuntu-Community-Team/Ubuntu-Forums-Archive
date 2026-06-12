---
title: "Setting up a good, efficient PHP Development Environment in Ubuntu"
date: 2009-02-28
forum: Programming Talk
---

### Post by JMisczak on 2009-02-28
I've done most of my limited development work (freelance and university-related) on Windows in the past. Does anybody have some pointers or even a guide on the best way to set up an efficient and productive PHP development environment on Ubuntu, or any distro?

---

### Post by Tibuda on 2009-03-01
I use this shell script to setup my local development server in Ubuntu. The comments explains everything.```
# Install Apache server
sudo aptitude install apache2

# Enable mod_rewrite (for friendly URLs)
sudo a2enmod rewrite

# Enable user directories like http://localhost/~username
sudo a2enmod userdir
mkdir -p $HOME/public_html
cp /var/www/index.html $HOME/public_html

# Install PHP 
sudo aptitude install php5 libapache2-mod-php5
echo "<?php phpinfo(); ?>" | sudo tee /var/www/info.php

# Restart Apache service
sudo service apache2 restart

# It should work now. Test it in your browser.
firefox http://localhost/info.php

# Install PEAR
sudo aptitude install php-pear

# Install GD
sudo aptitude install php5-gd

# If you want to use MySQL
sudo aptitude install php5-mysql mysql-server mysql-client mysql-query-browser

# If you want to use PostgreSQL
sudo aptitude install php5-pgsql postgresql-8.3 pgadmin3

# Restart Apache service again
sudo service apache2 restart

# Test it again in your browser.
firefox http://localhost/info.php

# Rapache is a settings GUI for Apache
sudo aptitude install rapache
```You probably have to change permissions in /var/www to start working there.

---

### Post by lzzncl88 on 2009-04-28
> **danielrmt said:**
> I use this shell script to setup my local development server in Ubuntu.
Thank you so much for your guide danielrmt : it worked out just perfectly!

(A really satisfied)* Nicolò*

---

### Post by rrll1977 on 2009-05-10
Hi All,

I am trying to get to work an out of the box apache+php+mysql server in xubuntu jaunty from the official jaunty repositories.

My problem is that **mod_rewrite** and **mod_userdir** were not enabled by default.

I did the following to enabled them.

```
#a2enmod rewrite
#a2enmod userdir
```

there was't a file caled rewrite.conf
 neither in **/etc/apache2/mods-available/** nor **/etc/apache2/mods-enabled/** so I created a empty file that called rewrite.conf, just in case, and made a symbolic link from **/etc/apache2/mods-enabled/rewrite.conf**
 to **/etc/apache2/mods-available/rewrite.conf**

```
#sudo ln -s /etc/apache2/mods-available/rewrite.conf /etc/apache2/mods-enabled/rewrite.conf
```

after that I changed all the “**AllowOverride None**” entries in **/etc/apache2/sites-enabled/000-default** to “**AllowOverride All**” without the quotes

and finally I restarted the apache server

```
#/etc/init.d/apache2 restart
```

after that I supposed that the mod rewrite had to be working so I write a little html and a .htaccess files to test it

It appears that the mod_rewrite is working but redirecting my pages to the absolute path of the website in the user directory

for instance [http://localhost/~user/test.html](http://localhost/~user/test.html) supposed to be redirected to [http://localhost/~user/index.html](http://localhost/~user/index.html), these are my .htaccess and index.html files

.htaccess
```
RewriteEngine On
RewriteRule ^(.*).html$ index.html [NC]
```

index.html
```
<html>
<body>
It Works !!!
</body>
</html>

```

but the browser shows the following error instead

```
Not Found
The requested URL /home/user/public_html/index.html was not found on this server.

Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80
```

Thanks in advice to anybody for your time and suggestions

---

### Post by jimi_hendrix on 2009-05-10
alternatively, there is xampp...

its a tar.gz that you get from the website, just unpack it where the website designates, run one command and it is up!

---

### Post by rrll1977 on 2009-05-11
Thanks, I definitely will give xampp a try on xubuntu.

I used to use xampp on windows, even the portableapps.com portable version, and I don't remember to have had such as troubles with htaccess and mod_rewrite.

Regards.

---

### Post by rrll1977 on 2009-05-13
> **rrll1977 said:**
> Thanks, I definitely will give xampp a try on xubuntu.

I used to use xampp on windows, even the portableapps.com portable version, and I don't remember to have had such as troubles with htaccess and mod_rewrite.

Regards.

Not solved yet... XAMPP with the same trouble.

mod_rewrite appears to work fine in root sites but not in user's.

---


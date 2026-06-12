---
title: "Can't open phpMyAdmin"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Neureo on 2008-07-14
I'm trying to install phpMyAdmin to use with my already-installed LAMP server. I used ```
$ sudo apt-get install phpmyadmin
```...which downloaded the software successfully, but when I try typing [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin), I get a 404. Apache is up and running smoothly, but how can I access phpMyAdmin?

---

### Post by Cypher on 2008-07-14
Have you also installed the PHP support?
```

sudo apt-get install libapache2-mod-php php5-mysql

```
Also, by default the phpmyadmin script is installed in /usr/share/phpmyadmin, a directory that isn't access from Apache.

You'll want to do the following to get [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to work
```

cd /var/www
sudo ln -s /usr/share/phpmyadmin phpmyadmin

```

---

### Post by OffAxis on 2008-07-14
phpmyadmin should all be lowercase (don't know if that's an issue on your server setup)
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

phpmyadmin also has an annoying habit of not putting a link into the web folder (I'm not sure what makes it not do that)

so you may need to go to your web folder root
```
cd /var/www/
```

and put one there yourself.
```
sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
```

---

### Post by RealG187 on 2009-11-13
```
cd /var/www
sudo ln -s /usr/share/phpmyadmin phpmyadmin
```Thanks that worked for me.

---

### Post by ramashema on 2010-07-21
thank you guyz:p it work....

---

### Post by hnmcc on 2010-08-10
...and this solution still works :D

> phpmyadmin also has an annoying habit of not putting a link into the web folder (I'm not sure what makes it not do that)

so you may need to go to your web folder root

```
cd /var/www/
```

and put one there yourself.

```
sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
```


---

### Post by Steve H on 2010-09-06
Worked a treat, thanks!!

I had to create the link by hand due to some weird permissions....but still worked!!

:D

---

### Post by manObject on 2010-09-09
> **OffAxis said:**
> phpmyadmin should all be lowercase (don't know if that's an issue on your server setup)
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

phpmyadmin also has an annoying habit of not putting a link into the web folder (I'm not sure what makes it not do that)

so you may need to go to your web folder root
```
cd /var/www/
```and put one there yourself.
```
sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
```

Thanks for this fix. Amazingly, as of todays date (9 September 2010) the problem is still there to trip up a Ubuntu newbie such as myself. Surely if all users are serving localhost out of /var/www/, why doesn't the phpmyadmin install script put the necessary files into /var/www/phpmyadmin automatically, or at the very least, flag up the issue as a comment in the terminal window during installation?

---

### Post by mulllhausen on 2010-10-14
i also had the problem of not being able to access phpmyadmin after i had installed it with ```
apt-get install phpmyadmin
``` (im using ubuntu 10.04.1 lts)

i found that the problem for me was that phpmyadmin had not created the necessary file 'phpmyadmin.conf' under /etc/apache2/conf.d. for me i had the advantage of being able to copy the file accross from another ubuntu system, however if you do not have this as an option the contents of this file are:

```
# phpMyAdmin default Apache configuration
Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options FollowSymLinks
    DirectoryIndex index.php

    <IfModule mod_php5.c>
        AddType application/x-httpd-php .php

        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals Off
        php_value include_path .
    </IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

```

i actually did ```
locate phpmyadmin | grep conf
``` just incase the file did infact exist with a different name - but no such luck.

---

### Post by delatun on 2010-10-14
Right, if you're having a trouble accessing after checking the paths are right in the Apache config, it's *probably *permission-related. ```
sudo chmod 777 directoryname
``` and work your way up from there. When you're diagnosing an issue like this, security (permissions) should never be tight unless your server is live and you want to add a few hours to the project, haha. I get trouble like that all the time with my Apache setup but the power of chmod cleans that right up!!

---

### Post by vikramk.ibs on 2011-09-20
It works!

Thanks a lot!
I am thinking to buy you :popcorn:

---

### Post by baubas101 on 2012-01-29
this worked for me too ;) THANKS ;)

> **OffAxis said:**
> phpmyadmin should all be lowercase (don't know if that's an issue on your server setup)
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

phpmyadmin also has an annoying habit of not putting a link into the web folder (I'm not sure what makes it not do that)

so you may need to go to your web folder root
```
cd /var/www/
```and put one there yourself.
```
sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
```

---

### Post by frtaljsira on 2013-02-25
> **Cypher said:**
> Have you also installed the PHP support?
```

sudo apt-get install libapache2-mod-php php5-mysql

```Also, by default the phpmyadmin script is installed in /usr/share/phpmyadmin, a directory that isn't access from Apache.

You'll want to do the following to get [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to work
```

cd /var/www
sudo ln -s /usr/share/phpmyadmin phpmyadmin

```

[COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] [COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] [COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] [COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] [COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] [COLOR=DarkGreen]**[SIZE=4]THANKS[/SIZE]**[/COLOR] =D>

This totally worked! :guitar:

---

### Post by oldos2er on 2013-02-25
Old thread closed.

---


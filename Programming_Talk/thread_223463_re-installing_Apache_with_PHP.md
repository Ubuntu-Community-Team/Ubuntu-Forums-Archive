---
title: "re-installing Apache with PHP"
date: 2006-07-26
forum: Programming Talk
---

### Post by rvbhute on 2006-07-26
I had successfully installed Apache2 with PHP. However when I tried to run the phpmailer utility (phpmailer.sourceforge.net), it gave me an SSL related error. I tried the php-cgi package but it didn't solve the problem plus now I can't get Apache2 to run php files, even with php installed as an Apache module - the file simply gets downloaded.

Right now I have completely removed all Apache and PHP modules from my setup. Any idea how to proceed from here?

---

### Post by mlind on 2006-07-26
Good idea would probably be to purge configuration files from both apache2 and php. use aptitude's purge. Then install them back,

---

### Post by rvbhute on 2006-07-26
I followed the purge instructions from  [this topic]("http://ubuntuforums.org/showthread.php?t=172023"). The following directories still remain -

[LIST=1]
[*]/etc/apache2, /etc/apache2/mods-available (with perl.conf and perl.load)
[*]/etc/php4/cgi (with php.ini) {I think installing php4-cgi broke my LAMP server}
[*]/var/www/html (contains only my stuff, Apache's default indexes have been removed)
[/LIST]

Should I remove these files/directories manually before proceeding with a re-install?

Also, does libapache-mod-php4 has support for OpenSSL? That is the reason I 'm writing this post...:p

---

### Post by mlind on 2006-07-26
Use dpkg -S to query what packages have left those files/folders behind and purge any apache2 & php related stuff.
```

dpkg -S /etc/php4/cgi/php.ini

```

To purge, you can use
```

sudo aptitude purge *package*

```

Don't remove any packages that cause major dependency errors. php package provides php5, not 4 (for Dapper).


```

aptitude show libapache2-mod-php5

```
seems to have OpensSSL support.

---

### Post by rvbhute on 2006-07-29
Followed your instructions - doesn't work. I'm obviously missing something right in front of my nose.

---

### Post by ifokkema on 2006-07-29
> **rvbhute said:**
> The following directories still remain -

[LIST=1]
[*]/etc/apache2, /etc/apache2/mods-available (with perl.conf and perl.load)
[*]/etc/php4/cgi (with php.ini) {I think installing php4-cgi broke my LAMP server}
[*]/var/www/html (contains only my stuff, Apache's default indexes have been removed)
[/LIST]
1) The perl.conf and perl.load are from libapache2-mod-perl2.
2) The /etc/php4/cgi/php.ini is from php4-cgi. This cannot be detected using dpkg -S or apt-file search, because the php.ini file is created by the post-install process. It's not in the package itself. If you want to get rid of it, this should work:
```
sudo apt-get remove --purge php4-cgi
```
or
```
sudo aptitude purge php4-cgi
```

> **rvbhute said:**
> Should I remove these files/directories manually before proceeding with a re-install?
No, but if you want to get rid of php4-cgi, uninstall that first.

> **rvbhute said:**
> Also, does libapache-mod-php4 has support for OpenSSL? That is the reason I 'm writing this post...:p
According to the package description... yes.

---

### Post by rvbhute on 2006-07-29
You guys have been very patient. Thanks. :D 

I think I have detected the problem (or the symptom atleast). The following is from my terminal

```
rohit@bhute:~$ sudo dpkg -S php5 | grep libapache2-mod-php5
libapache2-mod-php5: /usr/share/doc/libapache2-mod-php5
libapache2-mod-php5: /usr/lib/apache2/modules/libphp5.so
libapache2-mod-php5: /etc/apache2/mods-available/php5.load
libapache2-mod-php5: /usr/lib/php5/20051025
php5-common, libapache2-mod-php5: /usr/lib/php5
libapache2-mod-php5: /etc/php5
libapache2-mod-php5: /etc/apache2/mods-available/php5.conf
libapache2-mod-php5: /etc/php5/apache2
```

**But** php5.load and php.conf are missing - both in mods-available and mods-enabled. Think its time I placed them there by hand? Can you guys let me have a peek at php5.load and php5.conf?

---

### Post by mlind on 2006-07-29
libapache2-mod-php5 package contains both php5.load and php5.conf.
Just reisntall that package. If don't get the files this way, purge it and try again.

You can always download the package, and extract files from .deb if you're really desperate
```

mkdir /tmp/t
cd /tmp/t
aptitude download libapache2-mod-php5
dpkg -x libapache2-mod-php5 .
cd etc/apache2/mods-available/

```

---

### Post by ifokkema on 2006-07-29
> **rvbhute said:**
> 
```
rohit@bhute:~$ sudo dpkg -S php5 | grep libapache2-mod-php5
libapache2-mod-php5: /usr/share/doc/libapache2-mod-php5
libapache2-mod-php5: /usr/lib/apache2/modules/libphp5.so
libapache2-mod-php5: /etc/apache2/mods-available/php5.load
libapache2-mod-php5: /usr/lib/php5/20051025
php5-common, libapache2-mod-php5: /usr/lib/php5
libapache2-mod-php5: /etc/php5
libapache2-mod-php5: /etc/apache2/mods-available/php5.conf
libapache2-mod-php5: /etc/php5/apache2
```
If you want to view the list of files from a package, using
```
dpkg -L libapache2-mod-php5
```
is much faster.

> **rvbhute said:**
> **But** php5.load and php.conf are missing - both in mods-available and mods-enabled. Think its time I placed them there by hand? Can you guys let me have a peek at php5.load and php5.conf?
As mentioned by mlind, they are in mods-available. Mods-enabled contains softlinks, that are placed by scripts. To add these links to the mods-enabled directory (libapache2-mod-php5 needs to be installed correctly)
```
sudo a2enmod php5
```
This tells Apache to use the php5 module.

HTH

---

### Post by rvbhute on 2006-07-29
Guys, its fixed. Three lessons I learnt - trust the package tool, don't do anything manually that you will regret later; purge, purge and purge once more if you are not sure and lastly, when dealing with http, purge your browser's cache. The phpmailer package is also working well. Thanks.

---


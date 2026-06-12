---
title: "Empty httpd.conf in /etc/apache2"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Bucephalus01 on 2008-08-28
Hi

I have installed mysql, php, and apache2.
I did test php file put it in /var/www/ and then opened up firefox and [http://localhost/testphp.php](http://localhost/testphp.php)

It worked. I didn't even have to add php to the httpd.conf.
Since then I have installed Netbeans 6.5.
Now I can't read php files. I tried with html and it does work, so I know it's not picking up php files.
So I go to /etc/apache2/ and I vi httpd.conf
It's empty. I tried opening it with gedit after that and it's empty.
Where do I find this file so I can add php files? Or how do I fix this?

---

### Post by SomethingCronic on 2008-08-28
I 'think' apache2 doesn't use httpd.conf. It uses apache.conf instead - try looking in that file instead (the httpd.conf file is probably there for histrical reasons).

---

### Post by OffAxis on 2008-08-28
```
sudo a2enmod 
php5
```

should take care of that.

---

### Post by OffAxis on 2008-08-28
httpd.conf is deprecated.

the apache 2 configuration is kept in
**/etc/apache2/apache2.conf**

Configuration files for individual sites (1 per site) should be kept in 
**/etc/apache2/sites-available/**

and then enabled with 

```
sudo a2enmod
filename (usually the name of the site)
```
(which just places a link in the /etc/apache2/sites-enabled folder)

or disabled with 

```
sudo a2dissite
filename
```

---

### Post by kenlyle on 2009-10-04
In Jaunty, it seems to be /etc/httpd/conf/httpd.conf

Ken

---


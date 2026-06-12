---
title: "The mbstring extension is missing. Please check your PHP configuration."
date: 2017-03-09
forum: New to Ubuntu
---

### Post by recharde on 2017-03-09
i use ubuntu 16.04, i install properly phpmyadmin, but in browser i got this error.

---

### Post by slickymaster on 2017-03-09
Install **php-mbstring** and restart apache```
sudo apt-get install php-mbstring
sudo service apache2 restart
```

---

### Post by recharde on 2017-03-09
Ok thanks again after that i got this error "The [*mysqli|mysql*]("http://192.168.0.110/phpmyadmin/url.php?url=http%3A%2F%2Fphp.net%2Fmanual%2Fen%2Fbook.mysqli%7Cmysql.php") extension is missing."

---

### Post by slickymaster on 2017-03-09
Try to uncomment the line **mysqli.allow_local_infile = On** in php.ini and reboot.

---

### Post by recharde on 2017-03-09
same error again, i have 3 php version 5.6,7.0,7.1 i change every version in php.ini , and then restart and reboot the system but same error

---

### Post by slickymaster on 2017-03-09
Try```
sudo apt-get install php5-mysqlnd
sudo service apache2 restart
```

---

### Post by recharde on 2017-03-09
#sudo apt-get install php5-mysqlnd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php5-mysqlnd
i got this error.

---

### Post by Habitual on 2017-03-09
Try 
```
sudo apt-cache install php-mysqlnd
sudo service apache2 restart

```

---

### Post by recharde on 2017-03-09
Hello, [ 						 							]("https://ubuntuforums.org/member.php?u=504341")[**[COLOR=#000000]Habitual[/COLOR]**]("https://ubuntuforums.org/member.php?u=504341")
#sudo apt-cache install php-mysqlnd
E: Invalid operation install

---

### Post by Habitual on 2017-03-09
> **recharde said:**
> Hello, [                                                      ]("https://ubuntuforums.org/member.php?u=504341")[**[COLOR=#000000]Habitual[/COLOR]**]("https://ubuntuforums.org/member.php?u=504341")
#sudo apt-cache install php-mysqlnd
E: Invalid operation install

Doh,Sorry.
```
apt-get [COLOR=#000000][FONT=&quot]install php-mysqlnd[/FONT][/COLOR]
```

---

### Post by recharde on 2017-03-09
Again i got this error [**[COLOR=#000000]Habitual[/COLOR]**]("https://ubuntuforums.org/member.php?u=504341"),
#apt-get [COLOR=#000000][FONT=&amp]install php-mysqlnd[/FONT][/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php-mysqlnd is a virtual package provided by:
  php7.1-mysql 7.1.2-4+deb.sury.org~xenial+1
  php5.6-mysql 5.6.30-7+deb.sury.org~xenial+1
  php7.0-mysql 7.0.16-4+deb.sury.org~xenial+1
You should explicitly select one to install.

E: Package 'php-mysqlnd' has no installation candidate

---


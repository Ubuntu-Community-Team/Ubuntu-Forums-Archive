---
title: "sql file to big"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Joe67 on 2013-04-08
the sql file am trying to upload is to big, can anyone point me in the right direction how to upload it. cheers

---

### Post by zozzz on 2013-04-09
Where do you want to upload the file?
If you want import the sql file with phpmyadmin you can split it

---

### Post by SeijiSensei on 2013-04-09
You give us very little information to go on, but if you are using a web-based tool like phpmyadmin, then you are probably hitting the maximum upload size limitation in PHP.  If you have control over the server, look in /etc/php5/apache2/php.ini for the upload_max_filesize setting and increase it.  You'll need to restart the web server to make the change take effect.

---

### Post by Joe67 on 2013-04-09
aye its for myphpadmin how do you split it?

i had a look in etc/ but theres no folder called php5 pr myphp etc, anywhere else it could be located?

---

### Post by SeijiSensei on 2013-04-09
Try running "locate php.ini".

Is this an Ubuntu or Debian server, or a RedHat or CentOS server?  They put configuration files in different places.  On RH-flavored systems the file is /etc/php.ini.  On Ubuntu it resides in /etc/php5/apache2/.

Remember that this a file that resides on the server, not on the machine you are trying to upload from.

---

### Post by Joe67 on 2013-04-09
its a ubuntu server, there is no php5 folder in etc/


locate: can not stat () `/var/lib/mlocate/mlocate.db': No such file or directory
root@:~#

---

### Post by SeijiSensei on 2013-04-09
Apparently it is not building the locate database.  Try running "sudo updatedb", wait for it to finish, then try looking for php.ini again.

Or you could use one of the methods described [here](http://www.sudo-juice.com/where-is-php-ini/).

---

### Post by Joe67 on 2013-04-09
working now mate, thanks


/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini
/usr/share/doc/php5-common/examples/php.ini-development
/usr/share/php5/php.ini-production
/usr/share/php5/php.ini-production-dist
/usr/share/php5/php.ini-production.cli


edit: one last question :D where should i edit?


edit again:

; Maximum allowed size for uploaded files.
; [http://php.net/upload-max-filesize](http://php.net/upload-max-filesize)
upload_max_filesize = 2M  

??

---

### Post by SeijiSensei on 2013-04-09
That limits the filesize to 2 megabytes.  If you know how big the file you are uploading is, just change "2M" to something larger than your file like "20M".  Don't forget to restart Apache after making the change with
```
sudo service apache2 restart
```

---


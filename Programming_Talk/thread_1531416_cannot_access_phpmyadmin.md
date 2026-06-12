---
title: "cannot access phpmyadmin"
date: 2010-07-15
forum: Programming Talk
---

### Post by duceduc on 2010-07-15
I just installed ubuntu server 9.10 and started to install all my needed applications. I installed phpmyadmin using apt-get and followed the instruction. When I try to access it via htt://ip/phpmyadmin, I get my downloader dialogue box instead of the login page. It wants to download that file. Any idea how to fix this?

---

### Post by Yarui on 2010-07-15
Can you access it at [http://localhost/phpmyadmin?](http://localhost/phpmyadmin?)  If you can access it this way it points to something very different than if you can't.

---

### Post by lisati on 2010-07-15
> **duceduc said:**
> I just installed ubuntu server 9.10 and started to install all my needed applications. I installed phpmyadmin using apt-get and followed the instruction. When I try to access it via htt://ip/phpmyadmin, I get my downloader dialogue box instead of the login page. It wants to download that file. Any idea how to fix this?

From [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)
> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.

You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again. 

---

### Post by duceduc on 2010-07-15
> Can you access it at [http://localhost/phpmyadmin?](http://localhost/phpmyadmin?) If you can access it this way it points to something very different than if you can't.
I can't access it there either.

> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.

You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again.

It say php5 has already been enabled and libapache2-mod-php5 has been installed with the latest. I am still getting that prompt after a restart of apache.

Should I reinstall lamp at this point? 

Thanks guys.

---


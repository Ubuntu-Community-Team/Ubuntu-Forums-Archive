---
title: "phpmyadmin install problem"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by seanstuart on 2011-12-19
Complete newby to Linux, just installed apache2 for ubuntu, trying to install phpmyadmin but when i type [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  get this Error......404  File Not Found...?.. i am following these steps [http://connectwww.com/how-to-install-and-configure-apachephpmysql-and-phpmyadmin-on-ubuntu/727/ ]("http://connectwww.com/how-to-install-and-configure-apachephpmysql-and-phpmyadmin-on-ubuntu/727/")

Can you point me in the right direction...... Sean

---

### Post by kanikilu on 2011-12-19
With just a 404 error to go on, it's hard to say exactly what's wrong. However, the wiki offers the following suggestion:

> Should you get a 404 "Not Found" error when you point your browser to the location of phpMyAdmin (such as: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)) this is likely caused by not checking the 'Apache 2' selection during installation. To redo the installation run the following:
```
sudo dpkg-reconfigure -plow phpmyadmin
```

If that doesn't work, continue with the instructions here: [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---


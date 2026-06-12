---
title: "Ubuntu/Mysql/Wordpress problem"
date: 2019-09-02
forum: New to Ubuntu
---

### Post by barrysamuels on 2019-09-02
I have recently bought a new laptop which was supplied with Ubuntu 18.04.3 LTS (bionic) already installed. I didn't like the default desktop so I changed it to XFCE.


I have since installed Apache2, MySQL and Phpmyadmin. I have also installed a local copy of my web site, which includes a Wordpress blog, on this laptop. The web site is working as I would expect but I cannot reach the blog. The "Error establishing a database connection" message is displayed and, if I look in the MySQL logs I see "[Note] Access denied for user 'root'@'localhost'". The login details in the Wordpress configuration file are correct.


This is my first experience of Ubuntu although I also have a standard desktop computer running Debian Testing. There is also a local copy of my web site/blog on this desktop machine and everything runs as expected including access to the blog. There is also Apache2, MySQL and Phpmyadmin installed on the desktop.


I cannot see any reason for the problem in accessing the Wordpress blog on the laptop when it works as expected on the desktop running Debian. I would appreciate any advice.

---

### Post by SeijiSensei on 2019-09-02
> [Note] Access denied for user 'root'@'localhost'

[https://stackoverflow.com/questions/11760177/access-denied-for-root-user-in-mysql-command-line](https://stackoverflow.com/questions/11760177/access-denied-for-root-user-in-mysql-command-line)

Migrating a WP site is much easier if you use the Duplicator plugin: [https://wordpress.org/plugins/duplicator/](https://wordpress.org/plugins/duplicator/)

Create the migration package on the old machine, then create an empty MySQL database on the new machine. I strongly recommend using a unique username and password for the new database, not root.  Place the Duplicator package and its accompanying installer.php in the directory where the site will reside, then run installer.php from a browser. Duplicator will handle the rest.

---

### Post by barrysamuels on 2019-09-03
That was a very useful suggestion. I now have the blog working properly on my laptop. Many thanks.

---

### Post by SeijiSensei on 2019-09-03
The first time I migrated a site, I thought it would be easy to do manually as well.  It didn't take me long to discover that there are all sorts of hidden complexities in WP that something like Duplicator makes simple.  

You're welcome.

---

### Post by tanmoybiswas87 on 2019-09-03
Error establishing a database connection problem in xampp saver
I was facing this problem but now fixed.So i recommended this solution : [https://wordpress.stackexchange.com/questions/231680/error-establishing-a-database-connection-problem-in-xampp-saver](https://wordpress.stackexchange.com/questions/231680/error-establishing-a-database-connection-problem-in-xampp-saver)

---


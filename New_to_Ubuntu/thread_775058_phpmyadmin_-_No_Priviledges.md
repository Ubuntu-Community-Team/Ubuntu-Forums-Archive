---
title: "phpmyadmin - No Priviledges"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-04-29
Hi,

I have installed Ubuntu 8.04 server edition, webmin and phpmyadmin.

My problem is that when I try to create a new mysql database in phpmyadmin it says I have 'No Priviledges'.

I understand phpmyadmin doesn't create accounts etc. I have the password I created for MySQL when I created the LAMP server, but despite trying to login to phpmyadmin with my non-root username and both the mysql password and the normal linux password, it cannot gain access with an account which does have privileges.

If anyone can offer my some advice, it will be greatly appreciated.

thanks!

---

### Post by Ek0nomik on 2008-04-29
> **Swerve1000 said:**
> Hi,

I have installed Ubuntu 8.04 server edition, webmin and phpmyadmin.

My problem is that when I try to create a new mysql database in phpmyadmin it says I have 'No Priviledges'.

I understand phpmyadmin doesn't create accounts etc. I have the password I created for MySQL when I created the LAMP server, but despite trying to login to phpmyadmin with my non-root username and both the mysql password and the normal linux password, it cannot gain access with an account which does have privileges.

If anyone can offer my some advice, it will be greatly appreciated.

thanks!

The user your created apparently doesn't have permission to create database tables.  You need to create a user (or modify your existing one) to allow that user to create, and do anything else you want to the tables/database.

These might help:

[http://www.java2s.com/Code/SQL/User-Permission/CreateUser.htm](http://www.java2s.com/Code/SQL/User-Permission/CreateUser.htm)

[http://www.devarticles.com/c/a/MySQL/Creating-Users-and-Setting-Permissions-in-MySQL/2/](http://www.devarticles.com/c/a/MySQL/Creating-Users-and-Setting-Permissions-in-MySQL/2/)

[http://www.siteground.com/tutorials/php-mysql10/mysql_database_user.htm](http://www.siteground.com/tutorials/php-mysql10/mysql_database_user.htm)

---

### Post by Kolipoki on 2008-05-23
<-- Newbie here

I'm having the same problem. I installed the LAMP succesfully during setup, where 1 user was asked to be created with a password.

Later I installed PhpMyAdmin succesfully, but, it not only signs me   in with the user created during the Ubuntu setup _without a password_ (won't take the one created in the user server setup), it isn't showing the option for changing the users priviledges, showing instead the phrase "no priviledges" in red color.

Some of the links in the previous post don't apply. In one case the user is created thru a remote control panel (cPanel), and in another link, seems to me you will need the root user (disabled by default in Ubuntu, I'm trying to leave it like that, unless absolutely necessary).

I'm in the process of setting up a web server with a face to internet. Would greatly appreciate any help on this matter.

---


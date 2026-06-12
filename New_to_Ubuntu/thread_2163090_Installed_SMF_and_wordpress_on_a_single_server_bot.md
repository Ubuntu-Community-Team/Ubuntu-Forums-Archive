---
title: "Installed SMF and wordpress on a single server both in /var/www/"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by AguNnamdi on 2013-07-17
I used to access my wordpress before I installed SMF..After installing SMF, I can only access SMF but not wordpress( if go to [http://localhost/wp-admin](http://localhost/wp-admin))
Here is my directory :

agunnamdi@agunnamdi-Inspiron-N4050:/var/www$ ls
agreement.txt               news_readme.html    SSI.php
attachments                 Packages            subscriptions.php
avatars                     readme.html         Themes
cache                       Settings_bak.php    wordpress
index.php                   Settings.php        wp-admin
install_2-0_mysql.sql       Smileys             wp-content
install_2-0_postgresql.sql  Sources             wp-includes
install_2-0_sqlite.sql      ssi_examples.php
license.txt                 ssi_examples.shtml

Please I need the two of them to be running on my local computer.
Thanks.

---

### Post by Cheesemill on 2013-07-17
When you installed SMF you have overwritten some of the Wordpress files.

The easiest method to get them both working is to first of all restore the site to how it was from the last backup you made before installing SMF. You can then create a folder called /var/www/wordpress and move all of the contents of /var/www into it. Then create a folder called /var/www/smf and install SMF into this folder. You can then use [http://localhost/wordpress](http://localhost/wordpress) to access your Wordpress site and [http://localhost/smf](http://localhost/smf) to access your SMF site.

---


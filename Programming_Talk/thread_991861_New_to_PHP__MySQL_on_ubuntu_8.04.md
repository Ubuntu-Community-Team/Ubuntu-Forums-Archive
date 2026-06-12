---
title: "New to PHP / MySQL on ubuntu 8.04"
date: 2008-11-24
forum: Programming Talk
---

### Post by bravemenrun333 on 2008-11-24
Hello

I've set up a MySQL db with PhpMyAdmin on a server. I've installed Apache/MySQL/PHP on my ubuntu machine, everything works. How can I download the MySQL db to my computer, so I can edit it locally so I must not always upload it to test? I've also installed PhpMyAdmin locally, just don't know how to mirror the MySQL db to my computer. I understand that all I have to change within the php files is to change the server IP to "localhost". But where do I get the MySQL files from and where do I have to put them? Sorry for these newbie questions..

Thanks for any help
Bye

---

### Post by ufis on 2008-11-24
If you would like to have a copy or your remote db on your local box you can use the export feature of phpmyadmin on the remote db. This will enable you to save your remote db as a sql script on your box which you then use with the import feature of phpmyadmin to populate your local db.

If you would like to keep the 2 databases in sync you will need to read up on mysql replication. But that is a whole different ballgame.

---


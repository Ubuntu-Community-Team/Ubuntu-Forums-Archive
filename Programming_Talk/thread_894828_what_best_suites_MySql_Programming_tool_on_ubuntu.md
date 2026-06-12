---
title: "what best suites MySql Programming tool on ubuntu"
date: 2008-08-19
forum: Programming Talk
---

### Post by mshahien on 2008-08-19
Hi,
 i'm newbie on ubuntu,i want to decide which programming tools is the best to develop web applications on top of MySql database
thanks

---

### Post by FlyingIsFun1217 on 2008-08-19
Really depends on how you are accessing it. If you want direct interaction, go with the terminal. If you are using it through PHP, get a text editor with syntax highlighting. Etc.

FlyingIsFun1217

---

### Post by mshahien on 2008-08-19
hi,
i am accessing the mysql database from terminal, but can you advise me if there is a gui tool to create tables and run scripts?
also please specify a name of the PHP editor that i may use
thanks

---

### Post by Kadrus on 2008-08-19
Gedit is a good choice(the default editor,that comes with Ubuntu).
If you want to set up Apache with Mysql and PHP.
Take a look at [this guide.]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop")

---

### Post by cszikszoy on 2008-08-19
This is probably the best you're going to get as far as MySQL database administration:

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by brunovecchi on 2008-08-19
For automated queries, I use Perl with the DBI module.

---

### Post by tinny on 2008-08-19
> **cszikszoy said:**
> This is probably the best you're going to get as far as MySQL database administration:

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

IMO [MySQL GUI Tools]("http://dev.mysql.com/downloads/gui-tools/5.0.html") are better.

Also [MySQL Workbench]("http://dev.mysql.com/downloads/workbench/5.0.html") is great for Visual DB design (right now only available for windows).

[DBDesigner4]("http://www.fabforce.net/dbdesigner4/") is the Linux equivalent (MySQL Workbench is a fork of DBDesigner4).

---

### Post by pmasiar on 2008-08-19
for simple single-user apps, SQLite is simpler to use and manage than full server like MySQL. Depends what you need from database.

Ie Python+Django+SQLite is stack hard to beat, for simple apps.

---


---
title: "php+mysql &quot;undefined function mysql_connect()&quot;"
date: 2007-03-30
forum: Programming Talk
---

### Post by cleojb on 2007-03-30
Hi everyone, I'm a new user to this Furum.

I have that error message:

"Fatal error: Call to undefined function mysql_connect() in /var/www/cjbTest/myConnect.php on line 16"

line 16: mysql_connect('host', 'uName', 'pw') or die(mysql_error());
line 17: mysql_select_db(dbName) or die(mysql_error());

I did check the php.ini file and uncomment:
extension=mysql.so

But I do not know the location of mysql.so. And if I don't have the file (mysql.so), where can I download it?

I NEED HELP!!!

---

### Post by Monk-e on 2007-03-30
You need to install the package mysql-server

---

### Post by lnostdal on 2007-03-30
this is probably possible to do using the package manager directly, but i'm too lazy to bother figuring that out now .. so

* [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
* [http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=mysql.so&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=mysql.so&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)
..leading too..
* [http://packages.ubuntu.com/edgy/web/php5-mysql](http://packages.ubuntu.com/edgy/web/php5-mysql)

..as the most likely candidate i think.. so then you do:

```

sudo aptitude install php5-mysql

```

never ever(#1) "download" stuff when working in Linux; use the package manager of the distro you are using!


#1: there are some exceptions to this, but you better be damn sure you have a rationale for doing something like that.

---

### Post by cleojb on 2007-03-31
I would like to thank you both Monk-e and Inostdal. Now, everything works very well. BIG Thank you again for helping me; you are the best!!!

:) ):P

---


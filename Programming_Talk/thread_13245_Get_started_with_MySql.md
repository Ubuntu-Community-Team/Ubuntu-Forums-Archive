---
title: "Get started with MySql"
date: 2005-01-29
forum: Programming Talk
---

### Post by Ozitraveller on 2005-01-29
Anyone got any recommendations for getting started with MySql. I've had some experience with MSSql Server.

---

### Post by flyfishin on 2005-01-29
Install it and head over to the mysql.com site and click on the Developer link and the documentation section.

---

### Post by defkewl on 2005-02-17
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by Ozitraveller on 2005-02-17
[QUOTE=defkewl][http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)[/QUOTE]


Thanks. I've been there, and it is generally useful. I'm really looking for a small tutorial like article to get me started. Some that goes through an install, how to configure the Administrator, start/stop service,  and setup an existing database.

---

### Post by dataw0lf on 2005-02-17
[http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/](http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/)

Although MySQL is often touted as a great beginner SQL database system (and I agree), be aware of SQLite (good for templating and simple stuff) and Postgres (for when you start _really_ learning SQL).

dataw0lf

---

### Post by Ozitraveller on 2005-02-17
[QUOTE=dataw0lf][http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/](http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/)

Although MySQL is often touted as a great beginner SQL database system (and I agree), be aware of SQLite (good for templating and simple stuff) and Postgres (for when you start _really_ learning SQL).

dataw0lf[/QUOTE]


Thanks dataw0lf!

I'm ok with sql, I work with MS SqlServer, access, and I have done some work (a while back) on Oracle. So using the command-line for sql is now almost forgotten.

Firebird looks ok too....

---

### Post by blixtra on 2005-02-18
Getting started with MySQL is really easy.  First you want to install the mysql server.  Then you can start the server with this command:

```
sudo /etc/init.d/mysql start
```

Then, because intially the root user has no password, we want to set the password like this:

```
mysqladmin -u root password myPassword
```

You can now login to the mysql server with this:

```
mysql -u root -p
```

You'll need to type in the password that you entered earlier.

Every new MySQL install has 2 databases: mysql and test.  Do NOT screw up your mysql database because here is where all the permission and user info is.  The test DB is for you to play around with.  As was mentioned earlier the MySQL documentation is excellent.  That's the main reason I prefer it over the other 2 mentioned above (maybe their docs are better nowadays.) You'll probably want to set up a new user next. The MySQL docs can help you there.

You mentioned that you're familiar with SQL, so you should be able to play around now.

Chris

---

### Post by Ozitraveller on 2005-02-18
[QUOTE=blixtra]Getting started with MySQL is really easy.  First you want to install the mysql server.  Then you can start the server with this command:

```
sudo /etc/init.d/mysql start
```

Then, because intially the root user has no password, we want to set the password like this:

```
mysqladmin -u root password myPassword
```

You can now login to the mysql server with this:

```
mysql -u root -p
```

You'll need to type in the password that you entered earlier.

Every new MySQL install has 2 databases: mysql and test.  Do NOT screw up your mysql database because here is where all the permission and user info is.  The test DB is for you to play around with.  As was mentioned earlier the MySQL documentation is excellent.  That's the main reason I prefer it over the other 2 mentioned above (maybe their docs are better nowadays.) You'll probably want to set up a new user next. The MySQL docs can help you there.

You mentioned that you're familiar with SQL, so you should be able to play around now.

Chris[/QUOTE]

Thanks Chris. Much appreciated. I'll be trying this out today...

---

### Post by Ozitraveller on 2005-02-20
Well it's quick, isn't it! And on windows too! (this comment is for v4.1)

Does anyone know when v5, with StoredProcs will be out? I can't it to install.

---

### Post by ryharv on 2006-08-09
For what it's worth, I found the following MySQL tutorial extremely helpful.    It's written for both windows and linux users and takes you all the way from installation to all the basic tasks of using and administering databases.  I highly recommend it to someone who wants to learn MySQL but doesn't know where to start.

[http://www.webdevelopersnotes.com/tutorials/sql/downloading_mysql.php3]("http://www.webdevelopersnotes.com/tutorials/sql/downloading_mysql.php3")

---

### Post by StatusWoe on 2007-09-05
Thanks a ton this was nice and easy.

---

### Post by Krewie on 2008-08-24
Here is my tutorial on MySQL, simple and clean :D

[http://simplyeasy.wordpress.com/2008/08/24/mysql-basics/](http://simplyeasy.wordpress.com/2008/08/24/mysql-basics/)

---

### Post by JohnE1 on 2009-06-05
> **ryharv said:**
> For what it's worth, I found the following MySQL tutorial extremely helpful.    It's written for both windows and linux users and takes you all the way from installation to all the basic tasks of using and administering databases.  I highly recommend it to someone who wants to learn MySQL but doesn't know where to start.

[http://www.webdevelopersnotes.com/tutorials/sql/downloading_mysql.php3]("http://www.webdevelopersnotes.com/tutorials/sql/downloading_mysql.php3")

Good link. Thanks!

JohnE1

---

### Post by atom_box on 2009-06-15
> **dataw0lf said:**
> [http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/](http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/)

Although MySQL is often touted as a great beginner SQL database system (and I agree), be aware of SQLite (good for templating and simple stuff) and Postgres (for when you start _really_ learning SQL).

dataw0lf

Holy crow, as a beginner, I found that above link SUPER useful. Two months ago I didn't even know what a database was.  I have spent 3 frustrating mornings trying to get started with a SQL program. Gave up after 2 days of no good beginner documentation on postgreSQL and switched to MySql. MySql seems to have more documentation.  But then the cinch was your link, which was the most clear instructions I have read all week.  Your link worked great.   

I would add that, instead of downloading via RPM, I used the apt-get, as recommended on the MySql site.  I typed:
sudo apt-get install mysql-server
That worked very painlessly.

---

### Post by Dragonbite on 2009-06-15
This is just what I need. I haven't been too successful with MySQL yet.

---

### Post by Mirge on 2009-06-15
Also you might consider looking into "MySQL Query Browser", available in Ubuntu repo's... under mysql-query-browser I believe.

---

### Post by mejohnsn on 2009-09-07
> **blixtra said:**
> Getting started with MySQL is really easy.  First you want to install the mysql server.  Then you can start the server with this command:

```
sudo /etc/init.d/mysql start
```


Then, because intially the root user has no password, we want to set the password like this:

```
mysqladmin -u root password myPassword
```

You can now login to the mysql server with this:

```
mysql -u root -p
```

You'll need to type in the password that you entered earlier.

Every new MySQL install has 2 databases: mysql and test.


I just followed the install instructions at the top of this thread, and I got a 'mysql' database, but no 'test' database.

Even the directory /var/lib/mysql shows only 'mysql' and the databases I created myself, 'menagerie' (following the tutorial) and 'wvcmusiclibrary' (my own experimentation).

Just for reference, 'mysql --version' shows:

mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2.

---

### Post by ooolongT on 2010-02-12
I looked for two days for this: sudo /etc/init.d/mysql start

Works on Ubuntu too!


And for those of us who are a little slow, I also figured out after two days that if you dont set up a password, you need to login using:

User: root
PW: the root password for the computer

I know, I am not the brightest bulb in the bunch, but figured I would throw it out there anyway.

---

### Post by PhantomPhlier on 2010-02-17
I must be a dope - after successfully installing on Ubuntu and trying to set the admin password, I get:

bill-desktop:~$ mysqladmin -u root password <mynewpasswordhere>
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Tried restarting, stopping, starting (all appeared to work).  Checked the config, correct initial port, etc. as in all of the old posts.

Any ideas?

---

### Post by Hellkeepa on 2010-02-17
HELLo!

Sounds like the root user has a password set already.

Happy codin'!

---

### Post by mejohnsn on 2010-02-17
> **Hellkeepa said:**
> HELLo!

Sounds like the root user has a password set already.

Happy codin'!

Really? But then what does the message "Using password [NO]" mean? Does that only refer to his logon attempt, rather than to the security settings on his installation of MySQL?

As for what it does mean, I can only add this: it means he has network connectivity, he actually did get to 127.0.0.1 (no mean feat, even though this is the same as 'localhost'), he didn't firewall himsself into oblivion, but the MySQL server is refusing the connection.

I have always hated the error messages of MySQL. They are SO obscure and misleading!

So don't feel like a dope if you can't get this to work. This is the normal frustration of working with MySQL. Hang in there.

---

### Post by PhantomPholly on 2010-02-18
> **mejohnsn said:**
> Really? But then what does the message "Using password [NO]" mean? Does that only refer to his logon attempt, rather than to the security settings on his installation of MySQL?

As for what it does mean, I can only add this: it means he has network connectivity, he actually did get to 127.0.0.1 (no mean feat, even though this is the same as 'localhost'), he didn't firewall himsself into oblivion, but the MySQL server is refusing the connection.

I have always hated the error messages of MySQL. They are SO obscure and misleading!

So don't feel like a dope if you can't get this to work. This is the normal frustration of working with MySQL. Hang in there.

Thanks!  The root password did the trick - Doh!

---

### Post by Hellkeepa on 2010-02-18
HELLo!

**mejohnsn**: Yes, that error message reflects to that login attempt, and that attempt only. What it says, specifically, is that you did not provide the proper details to log in as the root password.
The "Using password [NO]" means that you didn't attempt to use a password in the login attempt, it says nothing about the status of whether or not the account has a password. That would be a rather big security issue, as it would make it trivial to figure out who have password protected their account, and who only relies on other means of restricting access.

Happy codin'!

---

### Post by jaya28inside on 2010-06-19
:confused:

i really got trouble now.
I thought it was done by installing mySQL from RPM using alien v.8.81
but, i got another prob, tough.

Is it possible that mysqld (or what we call daemon) is
not installed even we have done the mysql (server n client) installation via Alien?

seems most of the users got mysql from
synaptic or Ubuntu Software center using the internet connection... rather than downloading manual the RPM from mysql webpage, ... am i rite?

o gosh.

---

### Post by levis lover on 2010-06-26
can anyone please recommend a good book for sql ?
i would be using mysql on ubuntu ..

---

### Post by Hellkeepa on 2010-06-28
HELLo!

**jaya28inside**: Remove the RPM-based MySQL installation you've done, completely (purge). Then install it from the repo, like any other piece of software on *Ubuntu.

Happy codin'!

---

### Post by ruehara on 2010-07-14
> **levis lover said:**
> can anyone please recommend a good book for sql ?
i would be using mysql on ubuntu ..

O'Reilly have a good book - "MySQL & mSQL". Also there is a SAMS publication called "Teach yourself SQL in 10 minutes" The title is a bit optimistic but it's a handy pocket-sized reference.

I think mysql have a downloadable PDF manual which would be your best resource. In operation there is not a great deal of difference between any of the Linux variants.

---

### Post by suryagarlapati on 2010-10-20
after starting mysql . i cannot set the password with this command 
mysqladmin -u root password myPassword error getting is mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by jaya28inside on 2010-10-20
surely

why don't you just execute this one?

```
$> mysql -u root -p
```

ENTER! 

it will ask password, and type it, next ENTER again!
bravo!

---

### Post by buckyaustin on 2012-01-30
> **jaya28inside said:**
> surely

why don't you just execute this one?

```
$> mysql -u root -p
```

ENTER! 

it will ask password, and type it, next ENTER again!
bravo!

I made this file and put it on my desktop, so now all i have to do is double click and type my password. This then starts mysql. 

empty text file, renamed to MYSQL
[Desktop Entry]
Version=1.0
Type=Application
Name=MySQL
Comment=MySQL Database Design Tool
Exec=mysql -u root -p
Icon=/usr/share/mysql-workbench/images/MySQLWorkbench-48
Path=
Terminal=true
StartupNotify=false

I will be using a picture, but for ease of use since you wont have the same picture I left it out. Hope you enjoy. I couldn't have done that unless I read the comments here.

---

### Post by lisati on 2012-01-30
Abracadabra! And with that, the thread goes back to sleep.

---


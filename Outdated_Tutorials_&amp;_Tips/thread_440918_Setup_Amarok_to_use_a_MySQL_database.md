---
title: "Setup Amarok to use a MySQL database"
date: 2007-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Ashex on 2007-05-12
I just got done setting this up, and it was a wee bit tricky for me, as such I've decided to write a tutorial for others to use :)


First up, we want to install mysql

```

sudo apt-get install mysql-server mysql-client libmysqlclient12-dev
```

As soon as that is done and out of the way, we're going to want to set the password for the root account in mysql, just to be safe :)

```
mysqladmin -u root password NEWPASSWORD
```

And of course, instead of NEWPASSWORD, use your own :)

As soon as that is out of the way, we want to create a database and user for amarok to use.

```
mysql -p -u root
CREATE DATABASE amarok;
USE mysql;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
FLUSH PRIVILEGES;
```


For those of you who are using a remote server, you'll need to edit the my.cnf file to accept outside connection, as MySQL is by default set to only allow connections from localhost.

```
sudo nano /etc/mysql/my.cnd
```

Locate the line that appears as such:
> bind-address           = 127.0.0.1

And modify it to look as such:
> #bind-address           = 127.0.0.1

then restart the mysql service
```
sudo /etc/init.d/mysql restart
```

 We've now have a user and database setup for amarok to use. Time to open up amarok!

In amarok, go to settings> configure amarok
Click on the Collection icon in the left navigation bar.

Click the drop-down bar and select MySQL.

Use the following settings:
**Hostname**: 127.0.0.1
**Database**: amarok
**Port**: 3306
**Username**: amarok
**Password**: Your Password

*Note*: The default port for MySQL to accept connections is 3306, and use your own passowrd :)

Click Apply and you will now be connected to your own MySQL database :)

---

### Post by goodtimetribe on 2007-05-16
I couldn't get this to work. Either using a local fresh install of mysql or a new remote server and database either. Locally I got some errors on those mysql commands. Is that feisty? Should it matter? I wouldn't think so.

---

### Post by larsemil on 2007-05-18
your guide did not work for me either, allthough i got it working without any bigger problems myself. 

and changing to mysql amarok is so much faster now. really a big difference.

---

### Post by Dano18 on 2007-05-19
Your guide didn't work for me either, and I'm really wanting to get this straightened out.
Right now my problem is just installing mySQL, I haven't even gotten to Amarok yet.
I'm unable to install libmysqlclient12-dev.  When i try to apt-get install it, it responds with ```
Package libmysqlclient12-dev is not available, but is referred to by another package.

```
I found libmysqlclient15-dev in the synaptic and I installed that, but I'm still running into problems. Any help would be greatly appreciated, thanks.

---

### Post by likwid on 2007-05-19
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

There's a couple of semicolons missing from end of mysql commands.

---

### Post by Dano18 on 2007-05-19
Thanks likwid I got it working.  And to answer my own question, libmysqlclient15-dev does work instead of libmysqlclient12-dev.

---

### Post by asymmetric on 2007-05-24
just a note.. you should type

```

mysqladmin -u root -p create amarok

```

(**without database**)

then

```

mysql -u root -p

```

now you're logged in.

then

```

grant all on **amarok.*** to amarok@localhost identified by **yourpasshere ;** 
flush privileges**;**

```

**when in mysql, remember the semicolons ;**

that's  it
byez :)
asy

---

### Post by theseeker on 2007-05-25
> **asymmetric said:**
> 
then

```

grant all on **amarok.*** to amarok@localhost identified by **yourpasshere ;** 
flush privileges**;**

```

**when in mysql, remember the semicolons ;**

that's  it
byez :)
asy

When I type that, an error occurs:

```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'yourpasshere' at line 1

```

Why?

---

### Post by dave_walton on 2007-05-25
> **theseeker said:**
> When I type that, an error occurs:

```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'yourpasshere' at line 1

```

Why?

Try this:

$ mysql -p -u root
CREATE DATABASE amarok;
USE mysql;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
FLUSH PRIVILEGES;

---

### Post by rich.bradshaw on 2007-06-01
Yep, using offical amarok instructions works great. password is to be inside the ' s if you are wondering.

Nice speed up, and the coolness of mysql!

---

### Post by Ashex on 2007-06-02
I've updated the tutorial with various modifications. Sorry about the trouble guys!

---

### Post by walt+walt on 2007-07-06
I have tried this how-to with its different ways to configure mysql for amarok.

I think I got pretty far, but keep stopping at the password-entry. A selection of my tries is shown here:
----------------------------------------------------------------------------------------
root@ubuntu:~# mysqladmin -u root -p create amarok
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
root@ubuntu:~# mysqladmin -u root -p create amarok
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
------------------------------------------------------------------------------------------------

I do run feisty on desktop. I also reinstalled MySql a couple of times - cause I thought the prob is better solved with a blank version:  As Password I always used my root-password (single-machine - songle user).

Really, I have tried many forums but never found the clue.

Please, please help a grufty who has to show his guest that he's still alive and up-to-date. smile.

many thanks, walt

---

### Post by walt+walt on 2007-07-06
Ashex, you wrote:

[PHP]ve updated the tutorial with various modifications. Sorry about the trouble guys![/PHP]

where can I find the updated version?? I have tried the one at the beginning of this thread - but that didn't want to do it.

Many thanks for your assistance and cheeers, walt

---

### Post by g0kb3rk on 2007-09-19
Thanks for the topic and the tips, I got a question to ask (which doesn't have to be in a new topic). I don't recall that I set a password for the database and yet either if I did, I couldn't remeber what it was. 

[QUOTE=Code]
mysqladmin -u root password NEWPASSWORD
[/QUOTE]

after this code

[QUOTE=Reply]
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
[/QUOTE]

the reply is above. Is there something wrong that I did?

---

### Post by hfw on 2007-09-23
Thanks for the tutorial.  hopefully everything goes smoothly.  I love Amarok, but have always found it to be slow.  (I have about 30,000 tracks)  Hopefully the move to mySQL will help.  We will find out as soon as it finishes building the database.

hal

---

### Post by netimen on 2007-10-23
I want to reinstall my system switching from 64 bit Ubunt to 32 bit one. How do I transfer my amarok mysql database?

---

### Post by Lostincyberspace on 2007-11-05
Is it all on your system or do you want to keep a lot of podcasts. 

If its all on an accessible (after install) then just redo the config at the first start up. 

If you have a lot of podcasts to keep then backup you database in mysql (Google it, i don't remember the code) then replace after install and configuring of amarok (youmight not have to dothis but i think amarok might write overite if you don't)

Hope this helps I did the first with my system add it all went fine. Even over ntfs.

---


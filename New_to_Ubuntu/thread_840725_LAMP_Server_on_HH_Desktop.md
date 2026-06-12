---
title: "LAMP Server on HH Desktop"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by andyd34 on 2008-06-25
Hi all, I don't know if this is the right thread for this post, If not please forgive me..

I have istalled LAMP Server on Hary Heron Desktop, I get the apache2 side I even get the mysql side of it but my problem is I cannot access mysql. What I man is when I type 

> mysql --user=root mysql

I get the following

> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

When I open myphpadmin I can log in as root with my password but when I log in as me and use a password it throws up invalid. When i log in as me and no password I can log in but I have no privalages.

I thought it was the way I installed LAMP so I have wiped my HDD 4 times now and restarted from the beginning but each time I end up back where I started from.

I am very new to Ubuntu and Linux, I have always used Windows OS but decided it was time for a change. But I am beginning to think I am not cut out for it. If you can help please, please advice as this is going to be my last attemp before switching back to XP

---

### Post by spiderbatdad on 2008-06-25
The members who offer assistance in this forum are user/volunteers. I believe most of us do for enjoyment or because we like to help others. It is however, very tiring when someone comes along and threatens to go back to xp or whatever if he doesn't get help now. Go back to xp. Do whatever you want...like I care.

As to your issue: Have you set a root password for mysql?

```
mysql -u root
```

At the mysql console:

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

```
Note: If you have already set a password for the mysql root, you will need to use:

mysql -u root -p

(Did you forget the mysql-root password? See MysqlPasswordReset.)
Create a mysql database

mysql> CREATE DATABASE database1;

Create a mysql user

For creating a new user with all privileges (use only for troubleshooting), at mysql prompt type:

mysql> GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 

For creating a new user with fewer privileges (should work for most web applications) which can only use the database named "database1", at mysql prompt type:

mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database1.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword';

yourusername and yourpassword can be anything you like. database1 is the name of the database the user gets access to. localhost is the location which gets access to your database. You can change it to '%' (or to hostnames or ip addresses) to allow connections from every location (or only from specific locations) to the database. Note, that this can be a security problem and should only be used for testing purposes!

To exit the mysql prompt type:

mysql> \q

Since the mysql root password is now set, if you need to use mysql again (as the mysql root), you will need to use:

mysql -u root -p

and then enter the password at the prompt.

```


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by andyd34 on 2008-06-25
I am sorry if I offended anyone by saying I was thinking of going back to XP. I was not demanding help straight away. I was not even asking for direct help merely to be pointed in the right direction.

I have searched google for answers to many things regarding Ubuntu but I think with 8.04 Desktop being such a new variant there are few forums that offer the correct answers. I do like Ubuntu and in time I know I will master it but at the moment it is very frustrating coming from a Windows platform.

I would like to thank you for your suggestion and it is much appreciated, I undoubtedly will be posting more help request's in here until I find my feet with this platform but under no circumstances will I ever demand help.

---

### Post by spiderbatdad on 2008-06-25
Thanks for apologising. I apologise as well. I was probably the only person offended. It just gets old seeing...."this is the last straw before I go back to xp..." LOL.

Linux is definitely not xp or vista. There is a steep learning curve for new users, but there is with any OS initially. You're getting into some heavy stuff...more than most linux users will ever get into...so there is going to be a lot to learn with managing servers and databases...:)

Welcome to the forums. Please accept my apology.

---

### Post by andyd34 on 2008-06-28
Finally got it sorted but not by the conventional way. Ended up  installing phpmyadmin and setting the password there, i'm not to good on the command line.

I have done some decompiling using Borland C++ before but it was quite a while ago. Can you suggest any decompilers which UBUNTU supports so I can see how everything works. I am that sort of person, I remember the first day I got a PC, within 2 hours it was in bits on the kitchen table.

The reason I want a decompiler is to see if I can come up with some apps to make life easier, for argument sake if I want to edit a file it would be much easier selecting the file in a combo box from a certain directory then clicking a button saying edit that opening a terminal entering sudo gedit /somedir/somesub/anothersub/yetanothersud/thenthe.file dont you think.

---


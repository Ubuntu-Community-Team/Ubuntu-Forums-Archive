---
title: "mysql server?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-03
does anyone know how to configure amarok to work with mysql server? i can use it but i cant move anything to it...

---

### Post by dynamethod on 2008-07-03
first install mysql, then create a database called 'amarok', and configure amarok to use the username and password for that database

---

### Post by PatrickMoore on 2008-07-03
> **dynamethod said:**
> first install mysql, then create a database called 'amarok', and configure amarok to use the username and password for that database

first let me say nice quote.... ernesto guevara i believe?

 how do i set up the amarok database?

---

### Post by fatality_uk on 2008-07-03
Easy way to do this is is to install phpmyadmin from the repositories.
then type [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) into firefox
Setup a database from there

---

### Post by bhadotia on 2008-07-03
Just got it solved this morning :
[http://ubuntuforums.org/showthread.php?t=847686](http://ubuntuforums.org/showthread.php?t=847686)
 As an advice first try searching the forum before you post a new thread.

---

### Post by PatrickMoore on 2008-07-03
i will sorry about that. however im having problems with my username and password. now i cannot remember it is there a way to retrieve that?

---

### Post by bhadotia on 2008-07-03
The link I gave you above itself contains many links which are related to user names and password of database. Since You have forgotten the password I don't think there is any way to retreat it. 
Either just create a new account using the "root" user or just completely uninstall the mysql-server and start afresh with a new account.

---

### Post by PatrickMoore on 2008-07-03
> **bhadotia said:**
> The link I gave you above itself contains many links which are related to user names and password of database. Since You have forgotten the password I don't think there is any way to retreat it. 
Either just create a new account using the "root" user or just completely uninstall the mysql-server and start afresh with a new account.


 thats what i figured i think it would be easier to start fresh... thank you

---

### Post by bhadotia on 2008-07-03
Here for your convenience I am putting all the links here:
1 [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)
2 [http://ubuntuforums.org/showthread.php?t=847686](http://ubuntuforums.org/showthread.php?t=847686)
3 [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)
4 [http://dev.mysql.com/doc/refman/5.1/en/create-user.html](http://dev.mysql.com/doc/refman/5.1/en/create-user.html)

---

### Post by PatrickMoore on 2008-07-03
> **bhadotia said:**
> Here for your convenience I am putting all the links here:
1 [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)
2 [http://ubuntuforums.org/showthread.php?t=847686](http://ubuntuforums.org/showthread.php?t=847686)
3 [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)
4 [http://dev.mysql.com/doc/refman/5.1/en/create-user.html](http://dev.mysql.com/doc/refman/5.1/en/create-user.html)


ok im having one hell of a time with the  terminal trying to configure mysql. it seems to me that i cant do anything without confirmation. it just opens another line

---

### Post by bhadotia on 2008-07-03
Alright lets take it step by step . First tell me what is your position in the terminal . Just post the whole terminal output here so that we can see whats going on .

---

### Post by cariboo on 2008-07-03
Check the mysql docs. You have to end each command with a semi-colon **;**. If you don't it will just go to a new line.

Jim

---

### Post by bhadotia on 2008-07-03
> **cariboo907 said:**
> Check the mysql docs. You have to end each command with a semi-colon **;**. If you don't it will just go to a new line.

Jim
Yeah, forgot to tell you about that. I was also doing the same thing at first this morning (If you had a look at my thread in the link I gave).

---


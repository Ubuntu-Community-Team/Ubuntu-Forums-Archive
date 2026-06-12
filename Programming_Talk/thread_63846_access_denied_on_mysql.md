---
title: "access denied on mysql"
date: 2005-09-09
forum: Programming Talk
---

### Post by mabuti on 2005-09-09
Hello, I am very new to mysql and just recently installed it(mysql) on my Ubuntu useing the follwoing commands:

sudo apt-get install mysql-server
mysqladmin -u root password db_user_password

Firstly, would like to know what is the meaning and effects of the second command(mysqladmin). 
When I type the following:

mysql -h localhost -u root

, I get an error message, something like access denied.
Is there any howto on the net which explains how to handle accounts on mysql.

---

### Post by lao_V on 2005-09-09
By default mysql root doesn't have a password. You're not entering the system root password are you?

---

### Post by lao_V on 2005-09-09
You can find the mysql tutorial/guide at [mysql]("http://dev.mysql.com/doc/mysql/en/index.html")

---

### Post by mabuti on 2005-09-09
[QUOTE=lao_V]. You're not entering the system root password are you?[/QUOTE]
I don't follow. I simply copied and pasted the commands as they were on the guide([www.ubuntuguide.org)](www.ubuntuguide.org)).
sudo apt-get install mysql-server
mysqladmin -u root password db_user_password

---

### Post by lao_V on 2005-09-09
Are you substituting the db_user_password for the correct password?

---

### Post by mabuti on 2005-09-09
no, i didn't substiute it. Ohh, that's the user databases password. But which user is it, root? Bear with me, I am really new to this.

---

### Post by lao_V on 2005-09-09
As I said before, by default, mysql's root account doesn't have password. So you should be able to login using 

 ```
mysql -u root -h localhost
``` 

You don't need to provide the password argument. Then have a read at the mysql docs to find out how to create a new user, db, etc...You may find it easier to install phymyadmin which gives you web access to your mysql (you'll need to install apache as well)

Or if you want the full LAMPP solution then try [XAMPP]("http://www.apachefriends.org/en/xampp.html")

---

### Post by vayu on 2005-09-10
[QUOTE=mabuti]I don't follow. I simply copied and pasted the commands as they were on the guide([www.ubuntuguide.org)](www.ubuntuguide.org)).
sudo apt-get install mysql-server
mysqladmin -u root password db_user_password[/QUOTE]
 Since you set the password to db_user_password try this:

mysql -u root -p -h localhost

it should ask for the password, at which time you will enter: db_user_password

---


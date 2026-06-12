---
title: "Mysql backup script"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by mohan10 on 2013-08-05
Hi,

i installed mysql but i kept password as empty. now i need to set mysql backup command in cronjob with empty password.

mysqldump -u root -p dbname > /home/test/test.sql

The above command asking password to enter.

kindly provide a script to take mysql dump backup with empty password.

---

### Post by thespirit3 on 2013-08-05
-u <username> -p <password>

Have you tried omitting the -p?

mysqldump -u root dbname > /home/test/test.sql

edit: alternatively you may need to pass a blank password, perhaps mysqldump -u root -p "" dbname > /home/test/test.sql

---

### Post by fdrake on 2013-08-05
double post..

---

### Post by fdrake on 2013-08-05
have you tried :
mysqldump -u root -p $(echo -e "\0") dbname > /home/test/test.sq

[http://stackoverflow.com/questions/9293042/mysqldump-without-the-password-prompt](http://stackoverflow.com/questions/9293042/mysqldump-without-the-password-prompt) 
they all seem valid solution . especially the one with the shell script. just select an empy(no argument)

---

### Post by mohan10 on 2013-08-05
Hi,
mysqldump -u root dbname > /home/test/test.sql 
this worked.
thanks fri.

---

### Post by Cheesemill on 2013-08-05
Running mysql without a root password is a very bad idea as it leaves all of your databases wide open to attackers.

The best method of backing up a database is to create a mysql user specifically for the purposes of backing up and only giving it read permissions to your databases. You can then use the following command for your backup...
```
mysqldump -u backupuser -p password dbname > /home/test/test.sql
```

This way even if your backup script with the password in gets compromised then you aren't giving away full access to your database.

---


---
title: "Backing Up MySQL Databases"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by shanepardue on 2008-06-09
I am wanting to back up my Wordpress databases on my Ubuntu Server. What is 
the best way to get this done? I found the databases in /var/lib/mysql, but 
I'm skeptical if just copying those files would make a good backup. Also, I 
would like to steer clear of using a web interface as I want to eventually 
automate this process.

Thanks for any input!

---

### Post by cdtech on 2008-06-09
In a terminal type:
mysqldump -u username -ppassword wordpress > wordpress.sql

To re install the database do:
mysql -u username -ppassword wordpress < wordpress.sql

hope this helps.....

I run a dual Wordpress setup and script the backup to my laptop or vise versa along with databases.

---

### Post by shanepardue on 2008-06-09
> **cdtech said:**
> In a terminal type:
mysqldump -u username -ppassword wordpress > wordpress.sql

To re install the database do:
mysql -u username -ppassword wordpress < wordpress.sql

hope this helps.....

I run a dual Wordpress setup and script the backup to my laptop or vise versa along with databases.
Awesome! This is exactly what I'm looking for..I am running into a problem though. Is 
it a typo when you use the -ppassword argument? I've tried -p then the password, but 
I'm getting errors referencing the first character of my password.

Thanks!

---

### Post by cdtech on 2008-06-09
No typo...

Also if you want to download a database from your server onto your laptop persay:

 mysqldump -h yourserver.com -u username -ppassword wordpress > /var/www/wordpress/wordpress.sql

---

### Post by shanepardue on 2008-06-09
> **cdtech said:**
> No typo...

Also if you want to download a database from your server onto your laptop persay:

 mysqldump -h yourserver.com -u username -ppassword wordpress > /var/www/wordpress/wordpress.sql
Sorry, I know missing something..sorry for the ignorance. When you're saying -u username and -ppassword, am I to enter my username or password for the database?

Also, when pasting the command as you typed it, I get this error message..

> -bash: /home/myusername/wordpress.sql: No such file or directory

Thanks!

---

### Post by cariboo on 2008-06-09
Yes i think you are try

```
mysqldump -u username -p password wordpress > wordpress.sql
```

do this from your home directory so you can fimd it.

This is assuming that you are using the computer that the database is located on otherwise use:

```
mysqldump -h hostname_of_remote_computer - u username -p password wordpress > wordpress.sql
```

Hope this clears things up a little bit.

Just FYI the mysql databases are located in /var/lib/mysql

Jim

---

### Post by shanepardue on 2008-06-10
This is the command I use from the server containing the database..

> mysqldump -u usernameofdatabase -p actualpassword wordpress > wordpress.sql

And this is the error message I get...

> [1] 4643
-bash: wordpress.sql: Unknown error 526

---

### Post by cdtech on 2008-06-10
password should be -ppassword no space. And yes the command just copies the database wordpress to the dir wordpress with the name wordpress.sql.

Yes when you work with the database use the user and password you set for your mysql.

You should have set that up in wordpress config (database and password)

---

### Post by shanepardue on 2008-06-10
> **cdtech said:**
> password should be -ppassword no space. And yes the command just copies the database wordpress to the dir wordpress with the name wordpress.sql.

Yes when you work with the database use the user and password you set for your mysql.

You should have set that up in wordpress config (database and password)
Alright, I have found that wordpress.sql does in fact show up, but I still get this error message. Do you know why?

> [B] mysqldump -u sqlusername -pmypassword wordpress > wordpress.sql
Usage: mysqldump [OPTIONS] database [tables]
[1] 4712
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help
-bash: 4: command not found
[1]+  Exit 1 [/B]

Thanks, I really appreciate your help!

---

### Post by cdtech on 2008-06-10
What do you get when you just type:
sudo mysql

Should get the command prompt for mysql:
mysql>

Ok, update:
Use mysqldump -u username -ppassword --databases wordpress > wordpress.sql

Its a new thing....

---

### Post by shanepardue on 2008-06-10
Well, that's the root of my problem..no pun intended..here's my output.

> sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Without the password argument, could it be trying to use the mysql password when the root user of my machine has a different password? This is an Ubuntu Server so I'm not aware of the root user's password for that.

---

### Post by cdtech on 2008-06-10
system and MySQL root are different. They are separate and have nothing to do with each other.

If you have never set a root password for MySQL, MySQL does not require a password for connecting as root. To setup root password for the first time, use mysqladmin command at shell prompt as follows:
mysqladmin -u root password NEWPASSWORD

To change a root password, then you need to use the following command:
mysqladmin -u root -p oldpassword newpass

---

### Post by shanepardue on 2008-06-10
> **cdtech said:**
> system and MySQL root are different. They are separate and have nothing to do with each other.

If you have never set a root password for MySQL, MySQL does not require a password for connecting as root. To setup root password for the first time, use mysqladmin command at shell prompt as follows:
mysqladmin -u root password NEWPASSWORD

To change a root password, then you need to use the following command:
mysqladmin -u root -p oldpassword newpass
I know I already have a password set for the MySQL root account, but I've even tried "sudo mysql --password=myactualrootpassword" and I still get the following...

> [3] 5008
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
-bash: 4: command not found
[3]   Exit 1                  sudo mysql --password=myactualrootpassword


---

### Post by shanepardue on 2008-06-10
It appears as if my syntax is off, but I can't figure it out. I've read through a lot of the man page to no avail.

```
mysqldump -u myusername -pmyactualpassword --databases wordpress > wordpress.sql
Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help
[2] 5650
[2]-  Exit 1                  mysqldump -u myusername -pmyactualpassword
-bash: 4: command not found
[2]-  Exit 1                  mysqldump -u myusername -pmyactualpassword
```

---

### Post by cdtech on 2008-06-10
Hey shanepardue,

Can you even access MySQL's command prompt?
sudo mysql -u username -pyourpassword (should get you a command prompt)
show databases;
See if you even have any access to MySQL and that the actual database is listed.

---

### Post by cdtech on 2008-06-10
Try: which mysql
This will give you the path to mysql.

You may need to give the complete path to MySQL; /usr/bin/mysgl, on the command line.

To fix this, if this is the issue just update your path environment.

---

### Post by shanepardue on 2008-06-10
This gets me the MySQL prompt after it prompts me for a password
> sudo mysql --password

This gets mysqldump to work, but also prompts for a password..
> mysqldump -u root --password --databases wordpress > wordpress.sql

It seems the password argument is what's tripping me up. I'm now getting good backups (to my knowledge), but I'd like to be able to execute this command with a password prompt to simplify a cronjob.

Thank you so much!

---

### Post by cariboo on 2008-06-10
You should be able to do this as the user that you setup when you installed Wordpress, unless of course you used root as the user.

Jim

---

### Post by shanepardue on 2008-06-10
> **cariboo907 said:**
> You should be able to do this as the user that you setup when you installed Wordpress, unless of course you used root as the user.

Jim
The issue isn't with the username or any authentication-related. It's the way the 
password argument is being used. However I type my password into the command with the 
password argument, it still errors out thinking the password is a command or something.

---

### Post by shanepardue on 2008-06-13
Why is the -pPASSWORD argument tripping this command up? It gives an error like the command is incorrect.

> mysqldump -u myusername -pmyactualpassword --databases wordpress > wordpress.sql
Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help
[2] 5650
[2]-  Exit 1                  mysqldump -u myusername -pmyactualpassword
-bash: 4: command not found
[2]-  Exit 1                  mysqldump -u myusername -pmyactualpassword

---

### Post by shanepardue on 2008-06-21
I hate to keep posting worthless posts, but I'd really like to get my wordpress sites 
backed up automatically with cronjobs and without getting a password prompt each time.

---

### Post by shanepardue on 2008-07-10
I gotta keep bumping this because I'm stuck and I really need this utility to work. Do 
I need to redo the mysql databases to accomodate logging in correctly? As it stands 
now, any time I type my password in the command with the --password argument, it 
errors out.

Please help!

---


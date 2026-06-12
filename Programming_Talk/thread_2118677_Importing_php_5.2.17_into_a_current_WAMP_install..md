---
title: "Importing php 5.2.17 into a current WAMP install."
date: 2013-02-21
forum: Programming Talk
---

### Post by TechMansoor on 2013-02-21
Hello my brethren. Indeed had a really quick question. 

I'm trying to follow a lynda.com based tutorial and one thing I've already learned is that with certain versions of PHP 5, the syntax changes. So commands that work in 5.3.x will not necessarily work in 5.2.x.

IN any cse, I just installed wamp as the instructions metnioned, but I need for it to somehow recognize the 5.2.17 php I just installed so I can follow along with the tutorial.

Any suggestions/ideas would be invaluable!

Thanks everyone in advance!

---

### Post by dazman19 on 2013-02-22
i would remove wamp and install apache and your chosen version of php separately you will save time and there are good resources if you google it.

mysql is easy to install on window too.

if you can find a version of wamp with 5.2.17 then use that.

fyi debian 5 (lenny) installs php 5.2.17 as`standard when you run 
sudo apt-get install php5 so if you need to work in a php 5.2.17 environment just install a VM of debian 5. You will need to use the archives.debian.org repositories though as most mirrors wont have the code for debian 5 on them.

or you could just fix the code to work with 5.3/5.4.. it might be a better option.

---

### Post by TechMansoor on 2013-02-22
Thank you for the suggestiong dazman indeed. A guru locally  mentioned that I should stay pace with the 5.3 wamp install and when I run into a minor syntax update, I should just research the update.

Would your or anyone else concur with this philosphy? There isn't a truly big difference between the php versions?

The problem in particular I'm having is this:

> 
Hi all :) I am brand new and I just installed WAMP5_2.2
I am watching:Lynda.com.PHP.with.MySQL.Essential.Training.DVD-ViH and I am following
whatever happened on the video, but I am still getting the same error message.
I opened the MySQL console i wrote:

use mysql
UPDATE user
SET Password=PASSWORD('password')
WHERE user='root';

and I'm getting : ERROR 1064 <42000>: You have an error in your SQL syntax;check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE user='root'' at line 3 


everything goes fine up until i get to "WHERE user='root';"

then I get the following error as stated above..error 1064

---

### Post by SeijiSensei on 2013-02-22
That's not a PHP error.  It's a MySQL error.  Changing your PHP version won't fix this.

> You have an error in your SQL syntax;check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE user='root'' at line 3 

Did you, in fact, look in the relevant MySQL manual to see why this error occurs?  Here's the section on user management for [MySQL 5.5]("http://dev.mysql.com/doc/refman/5.5/en//adding-users.html").

Are you entering this command after running the "mysql" client program?  Are you running as the MySQL root user?

---

### Post by TechMansoor on 2013-02-22
> **SeijiSensei said:**
> That's not a PHP error.  It's a MySQL error.  Changing your PHP version won't fix this.



Did you, in fact, look in the relevant MySQL manual to see why this error occurs?  Here's the section on user management for [MySQL 5.5]("http://dev.mysql.com/doc/refman/5.5/en//adding-users.html").

Are you entering this command after running the "mysql" client program?  Are you running as the MySQL root user?

Fresh wamp install, running it as the default user in which you don't need a password to get into mysql.

I'll check out the manual, but I know its just an upgraded syntax spanning from php 5.2 to 5.3 or at least I'm deducing that..

---

### Post by dazman19 on 2013-02-22
try:
```

UPDATE mysql.user SET Password=PASSWORD('password')
  WHERE User='root' AND Host='localhost';
FLUSH PRIVILEGES;

```
You generally need to include the host.

e.g. when i make another user with full access I do this.
```

CREATE USER 'daz'@'localhost' IDENTIFIED BY 'somepass';
GRANT ALL PRIVILEGES ON *.* TO 'daz'@'localhost' WITH GRANT OPTION;

```

Its not a PHP problem

---

### Post by TechMansoor on 2013-02-22
> **dazman19 said:**
> try:
```

UPDATE mysql.user SET Password=PASSWORD('password')
  WHERE User='root' AND Host='localhost';
FLUSH PRIVILEGES;

```
You generally need to include the host.

e.g. when i make another user with full access I do this.
```

CREATE USER 'daz'@'localhost' IDENTIFIED BY 'somepass';
GRANT ALL PRIVILEGES ON *.* TO 'daz'@'localhost' WITH GRANT OPTION;

```

Its not a PHP problem

dazman you are amazing sir!! That did it!!! So the only difference it seems is that in your syntax you specified the host as being localhost.

Why didn't the original syntax as illustrated by the lynda.com teacher, work correctly? Is there a difference in Mysql versions that required me to specify the localhost??? Can you please explain my good sir so I may learn from my mistake.

Thank you so much. At least now I can go past lesson 1.

Thank you again!!

---

### Post by SeijiSensei on 2013-02-22
As far as I know, authentication in MySQL has been 'user'@'hostname' for quite a while.  The administrative user is typically 'root'@'localhost'.  If you want to give a username access from any host, you can specify rights for 'user'@'%' using the same wild-card character that applies in SQL LIKE clauses.

---


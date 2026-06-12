---
title: "PHP MySQL Connect to a Database Problem"
date: 2007-11-01
forum: Programming Talk
---

### Post by Kadrus on 2007-11-01
Euuh..I am having a problem connecting to a database using PHP

The script

<?php
$con = mysql_connect("localhost","username","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

if (mysql_query("CREATE DATABASE my_db",$con))
  {
  echo "Database created";
  }
else
  {
  echo "Error creating database: " . mysql_error();
  }

mysql_close($con);
?>


I am getting this error..

Could not connect: Lost connection to MySQL server at 'reading initial communication packet', system error: 111

If anyone can help me or anything..really appreciated :)

---

### Post by dataw0lf on 2007-11-01
Hmmm.  This is just a shot in the dark, but replace this line:

> $con = mysql_connect("localhost","username","password");

with this one:

```
$con = mysql_connect("127.0.0.1","username","password");
```
If that doesn't work, give me the output of the "sudo ifconfig -a" command.

---

### Post by Kadrus on 2007-11-01
> **dataw0lf said:**
> Hmmm.  This is just a shot in the dark, but replace this line:

;

with this one:

```
$con = mysql_connect("127.0.0.1","username","password");
```
If that doesn't work, give me the output of the "sudo ifconfig -a" command.
When I wrote "
$con = mysql_connect("127.0.0.1","username","password");
it gave me 

Could not connect: Access denied for user .....

---

### Post by Kadrus on 2007-11-01
> **Kadrus said:**
> When I wrote "
$con = mysql_connect("127.0.0.1","username","password");
it gave me 

Could not connect: Access denied for user .....

So any solution?

---

### Post by dataw0lf on 2007-11-01
> **Kadrus said:**
> So any solution?
Wait.  Are you actually using "username" and "password" in those fields?  They have to be an actual username and it's actual password (in the MySQL system, not the Linux system).  I think MySQL comes packaged with username "root" and password "", but it's been a while since I used it.

---

### Post by Kadrus on 2007-11-01
> **dataw0lf said:**
> Wait.  Are you actually using "username" and "password" in those fields?  They have to be an actual username and it's actual password (in the MySQL system, not the Linux system).  I think MySQL comes packaged with username "root" and password "", but it's been a while since I used it.

No I am not writing "username and password"

---

### Post by dataw0lf on 2007-11-01
So does the user and password you specified exist in MySQL?  My magic 8 ball says "Not likely".

---

### Post by Kadrus on 2007-11-01
> **dataw0lf said:**
> So does the user and password you specified exist in MySQL?  My magic 8 ball says "Not likely".
Yes

---

### Post by dataw0lf on 2007-11-01
Do you get any errors when you do:
```
mysql -u root mysql
```
from bash?

Are you able to perform a "SELECT * FROM user;"  if it does work? (and if it works, look for the username and password you specified).

---

### Post by Kadrus on 2007-11-01
> **dataw0lf said:**
> Do you get any errors when you do:
```
mysql -u root mysql
```
from bash?

Are you able to perform a "SELECT * FROM user;"  if it does work? (and if it works, look for the username and password you specified).

I get Access denied!

---

### Post by dataw0lf on 2007-11-01
Alright, perform these steps:

1) sudo bash

2) /etc/init.d/mysql stop

3) Run in bash:  echo "SET PASSWORD FOR 'root'@'localhost' = PASSWORD('SomeNewPassword');" >> ~/user.sql

Where SomeNewPassword is the new password you want for the MySQL root account

4) Run: mysqld_safe --init-file=~/user.sql &

5) Kill the mysqld_safe process (ps aux | grep mysqld_safe, get the process id, then kill -9 it)

6) Run: /etc/init.d/mysql start

7) try mysql -u root -p

8) Enter the password you supplied in step 3 when you are prompted for a password

It should connect then.

---

### Post by Kadrus on 2007-11-01
> **dataw0lf said:**
> Alright, perform these steps:

1) sudo bash

2) /etc/init.d/mysql stop

3) Run in bash:  echo "SET PASSWORD FOR 'root'@'localhost' = PASSWORD('SomeNewPassword');" >> ~/user.sql

Where SomeNewPassword is the new password you want for the MySQL root account

4) Run: mysqld_safe --init-file=~/user.sql &

5) Kill the mysqld_safe process (ps aux | grep mysqld_safe, get the process id, then kill -9 it)

6) Run: /etc/init.d/mysql start

7) try mysql -u root -p

8) Enter the password you supplied in step 3 when you are prompted for a password

It should connect then.
<snip>
When I type [http://localhost](http://localhost) in the url nothing appears anymore](*,):redface:

---

### Post by dataw0lf on 2007-11-01
Calm down.  Restart Apache.

---


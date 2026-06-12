---
title: "xampp mysql is not running"
date: 2018-02-28
forum: New to Ubuntu
---

### Post by niveshna2018 on 2018-02-28
[IMG]/home/nivi/Pictures/Screenshot from 2018-02-28 12-52-40.png[/IMG]

hi hello to everyone,
               i am new to ubuntu 16.04 LTS.i already installed xampp in ubuntu it works good.But the real problem is MYSQL .The mysql command line is working but along with php .it is not working.
please help me .i already tested a mysql connection test using php it "says unable to connect mysql" .I am already downloaded wordpress and installed it.but because of mysql error i can't come up with the solution pls help me:(:(
the following code:
XAMPP: Apache.......already running
XAMPP: starting mysql ....ok

it is not running but mysql command line in terminal is working.
and wordpress is also had some same mysql database error.

---

### Post by spjackson on 2018-02-28
Welcome to the forums.

mysql is running. This is confirmed by the startup message and also by fact that you can connect from the CLI. The problem could be the details for accessing the database that you provided when setting up Wordpress.

You used this formula for creating the user:
```

CREATE USER 'someuser'@'xxx.xxx.x.x' IDENTIFIED BY 'blah';

```

You almost certainly need 'localhost' instead of the IP address, unless you took some advanced steps when setting up mysql.

---

### Post by monkeybrain20122 on 2018-02-28
You don't need XAMPP on Ubuntu since you can easily install a LAMP stack on any Linux distro, IMO it is mainly for Windows.

---


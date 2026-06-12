---
title: "mysql problems"
date: 2012-09-12
forum: Programming Talk
---

### Post by WinterMadness on 2012-09-12
All I want to do is run mysql and test very basic things out, but mysql is fighting me every step of the way...

I dont think ive ever changed any settings since ive installed it, I just want to run mysql and look around etc

```
joe@joe-U46:/etc/init.d$ mysql
ERROR 1045 (28000): Access denied for user 'joe'@'localhost' (using password: NO)

```

I try:
```

mysql -u root -p mysql

```

I get:

```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

---

### Post by Bachstelze on 2012-09-12
Are you given the error straight away, or after typing a password? If you type a password, is the password correct?

---

### Post by Ryan Dwyer on 2012-09-15
When you installed mysql-server, what password did you set for the root user?

Maybe it's blank, in which case you should try it without the -p part: mysql -u root

If that doesn't work, run sudo dpkg-reconfigure mysql-server. That will run the setup choose-a-password thing that happened when you installed it.

---

### Post by josephmills on 2012-09-15
> **WinterMadness said:**
> All I want to do is run mysql and test very basic things out, but mysql is fighting me every step of the way...

I dont think ive ever changed any settings since ive installed it, I just want to run mysql and look around etc

```
joe@joe-U46:/etc/init.d$ mysql
ERROR 1045 (28000): Access denied for user 'joe'@'localhost' (using password: NO)

```

I try:
```

mysql -u root [COLOR="Red"]-p mysql[/COLOR]

```

I get:

```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

Needs to be jammed up against each-other 
```
mysql -h 127.0.0.1 -u username [COLOR="red"]-ppassword[/COLOR]
```
-h = host
-u for username 
-p password but make sure there is not "white space"

---

### Post by Bachstelze on 2012-09-16
> **josephmills said:**
> Needs to be jammed up against each-other 
```
mysql -h 127.0.0.1 -u username [COLOR="red"]-ppassword[/COLOR]
```
-h = host
-u for username 
-p password but make sure there is not "white space"

'mysql' is probably not the password (at least I hope so...).

---


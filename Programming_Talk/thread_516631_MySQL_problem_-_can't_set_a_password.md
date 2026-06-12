---
title: "MySQL problem - can't set a password"
date: 2007-08-03
forum: Programming Talk
---

### Post by KevinM1 on 2007-08-03
I've been trying to set my MySQL password, but I keep getting denied.  I'm using Ubuntu 7.04, MySQL 5.0.38.  I've tried the following terminal command:
> sudo mysqladmin -u root password myPassword

But have been getting the following error every time:
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

---

### Post by zanglang on 2007-08-03
It should be
> sudo mysqladmin -u root --password=myPassword

A safer way would be to omit your password and have mysql prompt for it, otherwise it can be easily seen in bash's history file
> sudo mysqladmin -u root -p

Edit: Silly syntax error. :|

---

### Post by KevinM1 on 2007-08-03
Unfortunately, the error still remains....
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I know the server is running, though, because I entered 'sudo /etc/init.d/mysql start' in the terminal and did not receive any error messages.

EDIT: for clarification, trying the 'password=myPassword' method results in the same error.  Trying 'sudo mysqladmin -u root -p' gives me a list of command-line options to use, but doesn't prompt me to set/enter a password.

---

### Post by jay019 on 2007-08-03
Misunderstood the problem.

For setting the password, I ended up just using myphpadmin on my webserver.
Not the best way, but it works.

---

### Post by KevinM1 on 2007-08-03
EDIT: D'oh, dueling edits!

---

### Post by zanglang on 2007-08-03
Ah sorry, I misread and thought you were trying 'mysql'. :P

Mysqladmin requires that you specify the command to run, e.g.
> mysqladmin -u root --password='abc' 'status'
or
> mysqladmin -u root -p 'status'
if you're omitting the password. Also, you don't really need to sudo.

Edit: Also if you're looking for the interactive interface for mysql, it's 'mysql'.

Edit 2: I just realized that my previous reply's syntax was wrong because I only noticed the "="... Anyway, it's "--password=", not just "password". :p

---

### Post by KevinM1 on 2007-08-03
> **zanglang said:**
> Ah sorry, I misread and thought you were trying 'mysql'. :P

Mysqladmin requires that you specify the command to run, e.g.

or

if you're omitting the password. Also, you don't really need to sudo.

Edit: Also if you're looking for the interactive interface for mysql, it's 'mysql'.

Edit 2: I just realized that my previous reply's syntax was wrong because I only noticed the "="... Anyway, it's "--password=", not just "password". :p

Ah, thanks!

Unfortunately, my phpMyAdmin problem remains (I know I didn't mention it before -- I needed to see if there was a MySQL password set first).  Should I describe the new problem here, or start a new thread?

---

### Post by KevinM1 on 2007-08-03
> **KevinM1 said:**
> Ah, thanks!

Unfortunately, my phpMyAdmin problem remains (I know I didn't mention it before -- I needed to see if there was a MySQL password set first).  Should I describe the new problem here, or start a new thread?

I think I solved my phpMyAdmin login problem.  I searched and found a thread by someone else with the same problem.  Apparently downloading php's mcrypt package fixes it.  It's working fine right now.

---


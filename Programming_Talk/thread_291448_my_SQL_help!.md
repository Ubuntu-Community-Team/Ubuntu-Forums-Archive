---
title: "my SQL help!"
date: 2006-11-02
forum: Programming Talk
---

### Post by pmcarson on 2006-11-02
Hello all,

I am in a beginning Linux programming class, and was playing around with mySQL.  My book told me to run the following commands

mysql> DELETE FROM mysql.user WHERE user != 'root';
mysql> DELETE FROM mysql.user WHERE host != 'localhost';

I was doing this assignment, but accidentally typed:

mysql> DELETE FROM mysql.user WHERE user != 'localhost';

and now I am unable to log in to mySQL.  I don't know what happened, but I am very frustrated.

Any input you have would be much appreciated.

Thx in advance.  ](*,)

---

### Post by yaaarrrgg on 2006-11-02
this might work (although I haven't tested it):

[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

### Post by pmcarson on 2006-11-02
Yay! it worked, thanks a bunch!

---

### Post by stashj on 2007-08-08
Perfect! I was expecting this to be a nightmare. I managed to remove the create user priveleges from the root user (don't ask :-)) but with a small mod to this I managed to put them back.

Thanks for the link!

---


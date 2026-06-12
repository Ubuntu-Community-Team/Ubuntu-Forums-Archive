---
title: "@ in MySQL"
date: 2007-12-15
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-15
I'm looking at [http://dev.mysql.com/doc/refman/5.1/en/xml-functions.html](http://dev.mysql.com/doc/refman/5.1/en/xml-functions.html) and I don't know what the @ means in them.  Anybody know?  Looks like it's a variable to me, but MySQL also uses the $ notation, so I'm not sure.  Doesn't look like an XPath @, to me, but maybe that's what it is.  I'm a n00b to MySQL and XML together, except for mysqldump --xml, which I've used before.

---

### Post by geirha on 2007-12-15
user-defined variables. [http://dev.mysql.com/doc/refman/5.0/en/user-variables.html](http://dev.mysql.com/doc/refman/5.0/en/user-variables.html)

---

### Post by tgilber1 on 2007-12-15
@variable is a means of setting user variables in MySQL.  The variables are only accessible to the user.  In other words, other mysql users will not be able to view the variable.

[http://dev.mysql.com/doc/refman/5.1/en/user-variables.html](http://dev.mysql.com/doc/refman/5.1/en/user-variables.html)

---

### Post by DouglasAWh on 2007-12-15
Great, thanks for the links!

---


---
title: "php and mysql"
date: 2011-04-14
forum: Programming Talk
---

### Post by ddmn on 2011-04-14
debugging on this php script line:
```
$con = mysql_connect("localhost", $dbUser, $dbPass) or die(mysql_error());
```i get the following error message:
```
PHP Fatal error:  Call to undefined function mysql_connect() in /path/to/file.php on line #
```what may be a problem here?

I'm running LAMP with eclipse as my IDE.
any solution to this problem?

---

### Post by BkkBonanza on 2011-04-15
You would likely only get that error if your version of php is missing the mysql module. Perhaps you only have mysqli installed instead? That is a different version of mysql routines that has different usage.

Make sure you have installed,

sudo apt-get install php5-mysql

After that it should have enabled the module automatically but you may want to check to be sure. There is more help here,

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---


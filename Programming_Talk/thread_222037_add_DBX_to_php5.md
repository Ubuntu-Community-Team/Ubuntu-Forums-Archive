---
title: "add DBX to php5"
date: 2006-07-24
forum: Programming Talk
---

### Post by mrphelps on 2006-07-24
I am attempting to install a script that uses the DBX module/extension for PHP.  Apparently this is no longer standard in newer versions of PHP.  How would I go about installing it on my server (Ubuntu 6.06 'Server' w/ LAMP)?

Here is the code from the db connection config:

[PHP]<?
class masterconfig	{
	function dbconnect(){
//type or adjust the "return dbx_connect ...." to match the pattern below
//		return dbx_connect(DBX_MYSQL,"<DB server address>","<name of database space, default is zci>","<DB username, default is zci>","<DB password, default is zci>");
//		default example :
 		return dbx_connect(DBX_MYSQL,"localhost","db","user","pw");

	}
}
?>[/PHP]

Here is a copy of my phpinfo page [http://myifdn.com/tmp/phpinfo.htm](http://myifdn.com/tmp/phpinfo.htm)

Any help would be greatly appreciated:mrgreen: .

---

### Post by stormchas3r on 2006-12-08
I am having the same problem trying to get zci working correctly.  Have you solved it yet?  I totally hosed my system trying to get dbx installed.

Please let me know,

Storm

---

### Post by folksilva on 2010-03-31
Follow this link:
[http://thinktube.wordpress.com/2009/03/24/dbx/](http://thinktube.wordpress.com/2009/03/24/dbx/)

---

### Post by dajhorn on 2010-07-16
I've packaged php-dbx for Ubuntu 10.04 Lucid here:

[INDENT][https://launchpad.net/~dajhorn/+archive/pecl](https://launchpad.net/~dajhorn/+archive/pecl)[/INDENT]

This is the ZCI dependency that is missing from Ubuntu.

---


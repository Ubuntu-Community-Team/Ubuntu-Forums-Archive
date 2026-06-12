---
title: "PHP and PostgreSQL programming issue"
date: 2007-04-09
forum: Programming Talk
---

### Post by gray-squirrel on 2007-04-09
I've been working on a migration script for some time to go from WordPress to Xaraya.  Over the past two and a half days I've made great progress (via my new Windows XP installation, so as to help with debugging and other matters).

I posted the [code elsewhere]("http://www.pastebin.ca/430646"), as I may get second opinions on this.

For about seven hours now, I can't seem to figure out what the problem is: everything runs fine until I get to line 238:

```
Fatal error: Call to undefined method ADORecordSet_postgres7::DATE_PART()
in /var/www/xaraya/import_wp_sql.php on line 238
```

Now, I already have the following items installed:

[LIST]
[*]PHP 5.2
[*]Apache 2.0.55 (Edgy) / 2.2.4 (Windows XP)
[*]PostgreSQL 8.2
[*]PostgreSQL support modules for PHP
[*]ADOdb
[/LIST]

I definitely have mod_auth for PostgreSQL installed on Edgy and Dapper, but that's not the problem because I've gotten this error on Edgy as well as on Windows, which more than likely does not have mod_auth for PostgreSQL.

I did a test PHP script, using the date_part function, without any reference to a database.  ```
<?php

	echo date_part('epoch',"4/8/2007");

?>
```resulted in  ```
Fatal error: Call to undefined function date_part() in /var/www/xaraya/test.php on line 3
```

This doesn't make any sense.  Apparently no error messages result from MySQL-specific functions (e.g. line 235).  Why is PHP acting this way?  I've spent hours searching, but the one or two possible solutions involved installing mod_auth and making sure PostgreSQL support was included in PHP, which have been taken care of.

---

### Post by Mirrorball on 2007-04-09
> **gray-squirrel said:**
> I did a test PHP script, using the date_part function, without any reference to a database.  ```
<?php

    echo date_part('epoch',"4/8/2007");

?>
```resulted in  ```
Fatal error: Call to undefined function date_part() in /var/www/xaraya/test.php on line 3
```This doesn't make any sense.
This part is easy: PHP doesn't have any function called date_part.
[http://www.php.net/manual-lookup.php?pattern=date_part&lang=en](http://www.php.net/manual-lookup.php?pattern=date_part&lang=en)
ADORecordSet_postgres7::DATE_PART() is an ADOdb function. Either your installed version of ADOdb doesn't have this function or you haven't included the file that defines it in your code.

---

### Post by Mirrorball on 2007-04-09
And this DATE_PART function isn't a member of the ADORecordSet class:
[http://phplens.com/adodb/reference.functions.adorecordset.html](http://phplens.com/adodb/reference.functions.adorecordset.html)

---


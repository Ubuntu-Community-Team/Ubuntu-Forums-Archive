---
title: "[PHP][MySQL] Stored procedures calling error"
date: 2007-02-04
forum: Programming Talk
---

### Post by brechtvb on 2007-02-04
I made myself a stored procedure in a mysql-db

```
CREATE PROCEDURE `getAantalReplies`(IN id INTEGER(11))
    DETERMINISTIC
    SQL SECURITY INVOKER
    COMMENT ''
BEGIN
SELECT COUNT(id)
FROM bericht
WHERE onderwerpid=id;
END;
```

```
$replies=mysql_query("call getAantalReplies(1)");
$obj=mysql_fetch_object($replies);
print mysql_error();
```

gives this:

```
Warning: mysql_fetch_object(): supplied argument is not a valid MySQL result resource in /var/www/volleybal/forum.php on line 26
PROCEDURE development.getAantalReplies can't return a result set in the given context
```

a normal sql-query (simple select) gives no problems

mysqli is installed (but i don't explicitly do mysqli_connect());

does anyone has an idea on this ?

---

### Post by ohgod on 2007-02-05
You're not calling mysql_connect() anywhere? (or did I misunderstand?)

EDIT:  Ignore me..

---

### Post by yaaarrrgg on 2007-02-05
You might get a better error message with:

```

$query = "call getAantalReplies(1)";
$qr1 = mysql_query ($query)
  or die ("Query failed: " . mysql_error() . " Query: " . $query);

```

---

### Post by ohgod on 2007-02-05
I tried the same thing and got the same error :(.  The stored procedure is not returning a result set in the same way a select statement does.  I'm not sure how to do this exactly.

If you you only need that one value back from your stored procedure, you might try an OUT paramter.

---

### Post by yaaarrrgg on 2007-02-05
hmmm... I did notice this on the the mysql docs page:

> 
For all of you getting "can't return a result set in the given context" errors when using PHP to execute stored procedures,
the mysql_connect flag is:

mysql_connect( host, databaseuser,password,TRUE, 131074)

Worked with mysql 5.0.20 and PHP 5.1.4
Also, stored procedures seem to close the connection when they've finished running in PHP.
Can be fixed using mysql_ping( db_resource_id ) to reinstate lost connections


From: [http://dev.mysql.com/doc/refman/5.0/en/stored-procedures.html](http://dev.mysql.com/doc/refman/5.0/en/stored-procedures.html)

I don't have php set up currently to test this though...

---

### Post by brechtvb on 2007-02-06
```
$spul=mysql_query("call getAantalReplies(1)");
$objspul=mysql_fetch_object($spul);	
print $objspul->aantal;
```

works with the

```
mysql_connect( host, databaseuser,password,TRUE, 131074)
```

command, i can use stored procedures, wich is a very good thing, though i use it in a mysql_pconnect() command, but i works

but my connection still get's closed after the stored-procedure-query

```

$query="select nickname from bericht where onderwerpid=1 order by tijd asc limit 1";
$starter=mysql_query($query) or die ("Query failed: " . mysql_error() . " Query: " . $query);
```

gives

> Query failed: Lost connection to MySQL server during query Query: select nickname from bericht where onderwerpid=1 order by tijd asc limit 1

---

### Post by yaaarrrgg on 2007-02-06
The notes said mysql_ping( db_resource_id ) might fix this....  i suppose you want to call this before the next query.

I wonder though... all this makes me think PHP driver is just a bit buggy.   Might try to use some of the other PHP db interfaces such as the built in mysqli_* functions, or PEAR:: DB or ADOdb ...

At the least, probably want to encapsulate all the code that interacts with the database into one place, since these solutions seem a bit hacky.  Something else might break in PHP in the next release, and you might need to rip all these fixes out :)

---


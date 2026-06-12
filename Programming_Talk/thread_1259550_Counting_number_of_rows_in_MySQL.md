---
title: "Counting number of rows in MySQL"
date: 2009-09-06
forum: Programming Talk
---

### Post by sdlynx on 2009-09-06
Hey guys,

This has nothing to do with Ubuntu (well a little  bit to do with Ubuntu but whatever), but I'm trying to count the number of rows I have in a MySQL database through PHP, and it keeps returning 5 (no the database does not have 5 entries).  This is my code for finding the number:
```
$count = mysql_query("SELECT COUNT(*) FROM table", $con);
```
Can anyone find a flaw in this, or have an alternative?

When running that line, I am already connected to the databases.

---

### Post by Bachstelze on 2009-09-06
```
$query = mysql_query("SELECT * FROM table", $con);
$count = mysql_num_rows($query);
```

---

### Post by Barrucadu on 2009-09-06
> **sdlynx said:**
> Can anyone find a flaw in this, or have an alternative?

The flaw is that mysql_query doesn't work like what you have assumed. The return value doesn't contain the results of the query, but a reference to the results. You'd probably have to use mysql_result() to get the count.

HymnToLife's suggestion will work.

---

### Post by sdlynx on 2009-09-06
> **HymnToLife said:**
> ```
$query = mysql_query("SELECT * FROM table", $con);
$count = mysql_num_rows($query);
```

Thanks! That worked.  And Barracudu I tried that mysql_result thing I think and it gave me some warning about it not being a supported argument or something.

---

### Post by Mateo on 2009-09-06
plus count(*) only gives you the number of rows on one particular table.  not all tables in the database.

---

### Post by falconindy on 2009-09-06
You may have misinterpreted what Baracuda meant by using mysql_result. He's absolutely right about a query only returning a reference to your results, and not the results themselves. You need to use the mysql_result (or one of several other methods) on the resource returned by a query, like so...
[php]$query = "SELECT COUNT(*) FROM table";
$result = mysql_query($query, $con);
echo mysql_result($result);[/php]
This should also give you the result you desire.

---

### Post by sdlynx on 2009-09-06
Now that that settled though, I have another problem.  I need to get the rows of the table that have a date of yesterday.  I keep a DATETIME field, and am not sure how to select only those rows from the earlier day.  I have tried the following but it returns 0 rows:
```
SELECT * FROM table WHERE dateTime>='CURRENT_DATE() - INTERVAL 1 DAY 00:00:00' and dateTime<='CURRENT_DATE() - INTERVAL 1 DAY 12:59:59' ORDER BY dateTime DESC LIMIT 0,15
```

I'd also like to do this for showing only the rows that belong to the current month.

---

### Post by unutbu on 2009-09-06
```
SELECT * FROM table WHERE cast(dateTime AS DATE)=cast(NOW() AS DATE)-1;
```

---

### Post by sdlynx on 2009-09-06
> **unutbu said:**
> ```
SELECT * FROM table WHERE cast(dateTime AS DATE)=cast(NOW() AS DATE)-1;
```

Unfortunately, this didn't work.  It returned ```
Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/sdlynxx/public_html/MLIN/index.php on line 182
``` when I tried to fetch the rows that it should have selected.

---

### Post by unutbu on 2009-09-06
I tested the command at a mysql command-line prompt. I believe the syntax is correct. 

The error you are receiving:
```

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource
```

seems to be saying the mysql_fetch_array function was expecting a "MySQL result resource".
My guess is that the SQL is okay, but the way you are passing it to the mysql_fetch_array function is wrong. 

I do not know PHP, but perhaps if you post the code for the mysql_fetch_array() call,
one of the blokes here can comment further.

---

### Post by sdlynx on 2009-09-06
```
$result = mysql_query("SELECT * FROM table WHERE cast(dateTime AS DATE)=cast(NOW() AS DATE)-1 ORDER BY dateTime DESC LIMIT 0,15", $con)
while($row = mysql_fetch_array($result)) {
echo $row[data] . "<br />";
}
```

That is my code exactly.  Anyone see an error?

---

### Post by unutbu on 2009-09-06
datetime is a MySQL keyword. Using it as a field name may be  getting MySQL confused. Perhaps try```


"SELECT * FROM table WHERE cast(`dateTime` AS DATE)=cast(NOW() AS DATE)-1 ORDER BY `dateTime` DESC LIMIT 0,15"
```

---

### Post by sdlynx on 2009-09-06
Real smart of me lol.  Well I tried what you said and still same problem.  However, I have tried ```
SELECT * FROM stories WHERE dateTime<=CURRENT_DATE() - INTERVAL '0' DAY and dateTime>=CURRENT_DATE() - INTERVAL '1' DAY ORDER BY nerdy DESC LIMIT 0.15
``` and it seems to be working. (It doesn't look like it should work, but it does...)

If anybody would like to take a look, [http://sd-lynx.co.cc/MLIN/](http://sd-lynx.co.cc/MLIN/) .
Hopefully I'll soon have my own TLD for it.

Assuming that works, I just need to know how to do the current month.

---

### Post by unutbu on 2009-09-06
sdlynx, I'm glad you found a way to get it to work!

Just out of curiosity, would you mind running the following mysql command? I'd like to see what error message you get.
```

SELECT * FROM stories WHERE cast(`dateTime` AS DATE)=cast(NOW() AS DATE)-1 ORDER BY nerdy DESC LIMIT 0,15
```

---

### Post by sdlynx on 2009-09-07
> **unutbu said:**
> sdlynx, I'm glad you found a way to get it to work!

Just out of curiosity, would you mind running the following mysql command? I'd like to see what error message you get.
```

SELECT * FROM stories WHERE cast(`dateTime` AS DATE)=cast(NOW() AS DATE)-1 ORDER BY nerdy DESC LIMIT 0,15
```

This also worked! Thanks, at least this one makes sense to me lol. I still need something for selecting rows for the current month, any ideas?

---

### Post by slavik on 2009-09-07
> **HymnToLife said:**
> ```
$query = mysql_query("SELECT * FROM table", $con);
$count = mysql_num_rows($query);
```
I wonder what will happen here when there are 300 million rows in a table ...

---

### Post by unutbu on 2009-09-07
sdlynx, I think this should pick off all rows that share the current year and month:
```
SELECT * FROM stories WHERE YEAR(`dateTime`)=YEAR(CURRENT_DATE()) and MONTH(`dateTime`)=MONTH(CURRENT_DATE());
```

---

### Post by sdlynx on 2009-09-07
> **unutbu said:**
> sdlynx, I think this should pick off all rows that share the current year and month:
```
SELECT * FROM stories WHERE YEAR(`dateTime`)=YEAR(CURRENT_DATE()) and MONTH(`dateTime`)=MONTH(CURRENT_DATE());
```

Thanks!! That worked great, which means that my whole website is complete ^_^

If anyone wants to take a look (I strongly suggest it) it's the second link in my sig.

---


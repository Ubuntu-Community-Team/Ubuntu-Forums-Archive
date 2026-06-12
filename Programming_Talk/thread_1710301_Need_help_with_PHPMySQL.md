---
title: "Need help with PHP/MySQL"
date: 2011-03-19
forum: Programming Talk
---

### Post by MyR on 2011-03-19
Hello,

I am developing a site for people to find [Linux-compatible printers]("http://linuxdeal.com/printers.php") and need some help.

I want to limit the number of results on the search page to about 15 and I want to display under the results something like "Displaying 16-30 of 47 results. << First  < Previous  Next >  Last >>"

Is it possible to have this functionality using only *one database query* instead of having a query to get the total number of results and one query with limit and offset to display the appropriately limited results?

Thanks

P.S.  Please submit your printer review!!

---

### Post by MyR on 2011-03-19
Nevermind, I'll go ahead with the two queries:

```
$page = ($_GET['page'])?$_GET['page']:'1';
$offset = ($page - 1)*15;
$result = mysql_query("SELECT * FROM Table1" . $query . " ORDER BY rating DESC LIMIT " . $offset . ",15");
$count = mysql_query("SELECT COUNT(*) FROM Table1" . $query);
$numberofresults = mysql_result($count, 0);

```

---

### Post by slavik on 2011-03-19
consider using prepared queries to minimize risk of sql injection attacks which your code is very prone to at the moment.

also, consider creating stored procedures for commonly used queries

---

### Post by Some Penguin on 2011-03-19
Agreed on use of prepared statements, provided that you may want to look into thread safety.  I'm not familiar at all with PHP's implementation of PSs and threading, but e.g. Java/JDBC allows only one active ResultSet per PreparedStatement, so interesting (undefined) things can happen when you attempt to execute the same PS in multiple threads.

Pagination via individual queries /is/ the right way to go with user-controlled pagination; it's much cleaner that way since you don't have to worry about either (1) fetching a gazillion results all the time most of which may never be looked at, or (2) keeping the result set, statement and connection all open until a timeout is reached.  'coz you can't fetch more results if you've already closed the result set.

---

### Post by MyR on 2011-03-19
> **slavik said:**
> consider using prepared queries to minimize risk of sql injection attacks which your code is very prone to at the moment.

also, consider creating stored procedures for commonly used queries

Admittedly I'm not very familiar with protecting against injection.  Do you have any recommended reading?  I've never heard of prepared statements.

---

### Post by slavik on 2011-03-19
first result from google returns the link to a page on php.net: [http://lmgtfy.com/?q=php+prepared+statements&l=1](http://lmgtfy.com/?q=php+prepared+statements&l=1)

---

### Post by Some Penguin on 2011-03-19
Obligatory:

[http://xkcd.com/327/]("http://xkcd.com/327/")

---

### Post by roadkillguy on 2011-03-20
Do you have a sequential id on each of the entries?

[PHP]
$query = "SELECT * FROM tableName WHERE [DEFINITELY PRESET] AND id > ".(int)page*15." AND id < ".((int)page + 1)*15." ORDER BY rating DESC";
[/PHP]

Forgive me for incorrect syntax, but will that not work?

---

### Post by MyR on 2011-03-20
> **roadkillguy said:**
> Do you have a sequential id on each of the entries?

[PHP]
$query = "SELECT * FROM tableName WHERE [DEFINITELY PRESET] AND id > ".(int)page*15." AND id < ".((int)page + 1)*15." ORDER BY rating DESC";
[/PHP]

Forgive me for incorrect syntax, but will that not work?

Each entry does have an id.  However the query is a search and is not intended to return all rows from the table.

My question is: is it secure enough to sanitize every $_GET parameter with something like preg_replace?

---


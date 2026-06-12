---
title: "php mysql"
date: 2014-02-28
forum: Programming Talk
---

### Post by bill-lancaster on 2014-02-28
I have lots of mysql data on my website and wish to access it using a php script.
phpmyadmin says I have one database 'lancasterfamily' and one of the tables is 'pgv_individuals'
If I run the following code (cobbled from a tutorial website):-
```
<?php
// Connecting, selecting database
$link = mysql_connect('localhost', 'username', 'pwd')
    or die('Could not connect: ' . mysql_error());
echo 'Connected successfully';

mysql_select_db('lancasterfamily.pgv_individuals') or die('Could not select database');

// Performing SQL query
$query = 'SELECT * FROM my_table';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());

// Printing results in HTML
echo "<table>\n";
while ($line = mysql_fetch_array($result, MYSQL_ASSOC)) {
    echo "\t<tr>\n";
    foreach ($line as $col_value) {
        echo "\t\t<td>$col_value</td>\n";
    }
    echo "\t</tr>\n";
}
echo "</table>\n";

// Free resultset
mysql_free_result($result);

// Closing connection
mysql_close($link);
?>
```
I get the following result:-
Connected  successfullyCould not select database

Any help would be much appreciated

---

### Post by bill-lancaster on 2014-02-28
That was stupid!  Publishing my password was not a good idea - I've now changed it.

---

### Post by Habitual on 2014-02-28
> **bill-lancaster said:**
> That was stupid!  Publishing my password was not a good idea - I've now changed it.
You should edit the original post and either remove it, or just use <password> there.

and your selecting a db.table here?
```
mysql_select_db('lancasterfamily.pgv_individuals'
``` so try just
```
mysql_select_db('lancasterfamily') or die('Could not select database');
```
or should that be
```
mysql_select_db('pgv_individuals') or die('Could not select database');
```?

What is the db name?

found an old link with this basis as an example. :)
[PHP]<?php
$link = mysql_connect('server.com', 'mysql_user', 'mysql_password');
if (!$link) {
    die('Could not connect: ' . mysql_error());
}
echo 'Connected successfully';
mysql_close($link);
?>[/PHP]


```
php -f test.php
```
Connected successfully

---

### Post by bill-lancaster on 2014-03-01
Thanks for the ideas.  Have change my post as sugested as well as the db password!

```
mysql_select_db('lancasterfamily') or die('Could not select database');
```
Gives:-
"Connected successfullyQuery failed: Table 'lancasterfamily.my_table' doesn't exist"

Also:-
```
mysql_select_db('pgv_individuals') or die('Could not select database');
```
produces:-
"Connected successfullyCould not select database"

I also found that old link, the code runs fine - I get get a connection.
Adding further code to open a database gives me the same problems.

Running phpMyAdmin on my webspace provider's control panel shows one database - 'lancasterfamily'

---

### Post by bill-lancaster on 2014-03-01
OK - don't know what I was doing wrong but now have full access to database
Thanks for the help.

---

### Post by Dimarchi on 2014-03-06
For further reference, trying to make Habitual's answer a bit more clear...

**mysql_select_db** requires a database, which seems to be *lancasterfamily*. That database has tables *(pgv_individuals*, at least). You need to select database first for mysql to know what tables should be queried. *lancasterfamily.pgv_individuals* is not a database, it is a table *(pgv_individuals* table of *lancasterfamily* database). Therefore...

```
mysql_select_db('lancasterfamily') or die('couldn't select db');
```

When you are ready (the database is selected), you can start queries. Both of these are ok...they are, in fact, the same query:

```
$query = "SELECT * FROM pgv_individuals";
```

and

```
$query = "SELECT * FROM lancasterfamily.pgv_individuals";
```

If you were to try querying the following:

```
$query = "SELECT * FROM someotherfamily.pgv_individuals";
```

it would not work. Why? Becase you have selected and opened the *lancasterfamily* database, not *someotherfamily* database (should it even exist). You need to do your stuff (queries) in the *lancasterfamily* database first, close it, and open *someotherfamily* database (using **mysql_select_db**) and do your queries there.

---

### Post by Habitual on 2014-03-06
> **Dimarchi said:**
> You need to do your stuff (queries) in the *lancasterfamily* database first, close it, and open *someotherfamily* database (using **mysql_select_db**) and do your queries there.or change the select statement slightly using ```
select * from db_name:table_name;
``` Just prefix db_name if you're moving about dbs and their tables.

---


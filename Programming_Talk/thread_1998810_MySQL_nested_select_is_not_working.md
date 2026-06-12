---
title: "MySQL: nested select is not working"
date: 2012-06-07
forum: Programming Talk
---

### Post by anon0 on 2012-06-07
I have a table 'mytable' with two columns, 'name' and 'value'.
I want to select all 'name' of rows whose value = max(value)

If I do it without a nested select, it works correctly:
SELECT MAX(value) FROM mytable
store this value in PHP as $max_value
then do,
SELECT name FROM mytable WHERE value = '$max_value'

But when I tried to do a nested select, it failed. I've tried:
SELECT name
FROM mytable
WHERE value = (SELECT MAX(value) FROM mytable);

SELECT name
FROM myTable
WHERE value IN (SELECT max(value) FROM myTable)

Both failed to retrieve any rows, even though some suggested that the syntax seem ok at a glance. The MySQL version is 5.1.58-1ubuntu1.

Any ideas?

---

### Post by steeldriver on 2012-06-07
I happen to have a mythconverg database open right now and the syntax seems to work for me

```
mysql> SELECT title, filesize 
    -> FROM recorded WHERE filesize = (SELECT MAX(filesize) FROM recorded);
+-------------+-----------+
| title       | filesize  |
+-------------+-----------+
| TVO Program | 391399456 |
+-------------+-----------+
1 row in set (0.00 sec)

```

my version is 5.1.62-0ubuntu0.11.10.1

What type is your 'value' though? I wonder if there's something going on with rounding or truncation?

---

### Post by anon0 on 2012-06-07
Thanks, I noticed that the same query works in phpmyadmin but not in PHP. However, the one in PHP is a temporary table. I used a mock table with the same columns for testing in phpmyadmin.

The weird thing is that the table works if I do it in PHP in two steps:

$query_result = mysql_query("
SELECT MAX(value)
FROM temp_table
");
$row = mysql_fetch_array($query_result, MYSQL_ASSOC);
$max_value = $row['MAX(value)'];

$query_result = mysql_query("
SELECT name, value
FROM temp_table
WHERE value = 'max_value'");


Why can't I do it in one step like I can in phpmyadmin, like this:

SELECT name, value 
FROM table 
WHERE value = (
SELECT MAX(value)
FROM table
)


...
Edit: I have confirmed that this is an issue with temporary tables in MySQL:
"You cannot refer to a TEMPORARY table more than once in the same query."
[http://dev.mysql.com/doc/refman/5.0/en/temporary-table-problems.html](http://dev.mysql.com/doc/refman/5.0/en/temporary-table-problems.html)

---

### Post by davetv on 2012-06-07
Thanks for your question and answer anon0. I had been trying to duplicate your problem (for fun and learning), but couldn't.

Limitation of temp tables hey - I learn something new every day.

---


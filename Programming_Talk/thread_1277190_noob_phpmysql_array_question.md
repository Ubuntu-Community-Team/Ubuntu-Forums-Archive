---
title: "noob php/mysql array question"
date: 2009-09-28
forum: Programming Talk
---

### Post by lunaz on 2009-09-28
i'm going thru the o'reilly php & mysql book (2nd ed). all's well til example on page 186.

i'm not sure where the numbers in the array index come from.

```

// Fetch and display the results
while ($result_row = mysql_fetch_row(($result))){
       echo 'Title: '.$result_row[1] . '<br />';
       echo 'Author: '.$result_row[4] . '<br /> ';
       echo 'Pages: '.$result_row[2] . '<br /><br />';
}

```

it runs ok but i think i'm missing where the [1],[4],[2] come from.

i logged into the mysql command line & ran the same query from the book:

```
SELECT * FROM books NATURAL JOIN authors;
```

 and it showed:

```

mysql> SELECT * FROM books NATURAL JOIN authors;
+----------+-------------------------+-------+-----------+------------

----+
| title_id | title                   | pages | author_id | author      

   |
+----------+-------------------------+-------+-----------+------------

----+
|        1 | Linux in a Nutshell     |   112 |         1 | Ellen 

Siever   |
|        1 | Linux in a Nutshell     |   112 |         2 | Aaron Weber 

   |
|        2 | Classic Shell Scripting |   256 |         3 | Arnold 

Robbins |
|        2 | Classic Shell Scripting |   256 |         4 | Nelson 

Beebe   |
+----------+-------------------------+-------+-----------+------------

----+
4 rows in set (0.00 sec)

```

---

### Post by korvirlol on 2009-09-28
There are typically 2 ways to access fields returned for each row in a query. The standard array index with integers (your example) and associative arrays.

In your example, the fields correlate to index:

title_id => 0
title => 1
pages => 2
author_id => 3
author => 4

so, when you call something like: 
[FONT=monospace]$result_row[4] you are returning the author in each tuple selected.

This works fine, but im a fan (and i think most developers) of associative arrays. Makes reading the code a lot easier... ESPECIALLY if you are debugging someone elses code.

Alternatively, to access the same thing, you could go:

$result_row['author'].

hope this helps
[/FONT]

---

### Post by v8YKxgHe on 2009-09-28
Just a note, mysql_fetch_row() will not return an associative array, you need to use mysql_fetch_assoc() for that.

---

### Post by lunaz on 2009-09-28
sweet, that makes sense, thanks for the replies :)

---


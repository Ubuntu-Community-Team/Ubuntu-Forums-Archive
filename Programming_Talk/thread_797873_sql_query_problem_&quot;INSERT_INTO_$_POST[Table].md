---
title: "sql query problem &quot;INSERT INTO $_POST[Table]"
date: 2008-05-17
forum: Programming Talk
---

### Post by saj0577 on 2008-05-17
```
$query=("INSERT INTO $_POST[Table] (Title, Date, Content)
VALUES ('$_POST[Title]', '$_POST[Date]', '$_POST[Content]')");
```



I know the $_POST[Table] is whats causing the problem so could you please tell me how I make it work.

Thanks alot

Saj

---

### Post by scxtt on 2008-05-17
not 100% sure, but ...
[php]$query = "insert into $_POST[\"Table\"] (`Title`, `Date`, `Content`) VALUES ('$_POST[\"Title\"]', '$_POST[\"Date\"]', '$_POST[\"Content\"]')";[/php]

---

### Post by dwhitney67 on 2008-05-17
If I had to guess, I would say that all of your _POSTs are wrong.  Try something like:

```

$query="INSERT INTO ".$_POST["Table"]." (Title, Date, Content) "
       ."VALUES ('".$_POST["Title"]."', '".$_POST["Date"]."', '".$_POST["Content"]."');";

```

P.S.  PHP ought to be renamed to POS.  Too many quotes... so damn hard to read.

---

### Post by saj0577 on 2008-05-17
Both cause errors :(

Saj

---

### Post by dwhitney67 on 2008-05-17
Try copying/pasting my previously submitted answer again... I had to edit it.  Should work now.

---

### Post by bvanaerde on 2008-05-17
Maybe a silly question, but why would you work like this? Using posted variables directly in an SQL query?

Apart from that, dwhitney67's post seems to be correct.

---

### Post by MicahCarrick on 2008-05-17
Also suggesting to not put any POST variables directly into a MySQL statement. 

Just want to make a point that some people like using curly braces when putting complex variables into strings that will be parsed. Just another way of doing the same thing.

```

$query="INSERT INTO {$_POST['Table']} (Title, Date, Content) 
        VALUES ('{$_POST['Title']}', '{$_POST['Date']}',
        '{$_POST['Content']}')";

```

---

### Post by saj0577 on 2008-05-17
How do u suggest to have a form i can use for submiting the same type of information but into different tables then please?


Saj

---

### Post by dwhitney67 on 2008-05-17
I agree with bvanaerde and MicahCarrick.

Here's a query that is easier to read:
[PHP]
$table   = $_POST["Table"];
$title   = $_POST["Title"];
$date    = $_POST["Date"];
$content = $_POST["Content"];

$query   = "INSERT INTO $table (Title, Date, Content) VALUES ('$title', '$date', '$content');";
[/PHP]

---

### Post by saj0577 on 2008-05-17
or i want the table to be decided by a cookie or a session.

Saj

---

### Post by saj0577 on 2008-05-17
> **dwhitney67 said:**
> I agree with bvanaerde and MicahCarrick.

Here's a query that is easier to read:
[PHP]
$table   = $_POST["Table"];
$title   = $_POST["Title"];
$date    = $_POST["Date"];
$content = $_POST["Content"];

$query   = "INSERT INTO $table (Title, Date, Content) VALUES ('$title', '$date', '$content');";
[/PHP]


> 
Error: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(Title, Date, Content) VALUES ('tster1233', '2008-05-17', 'ggegergergrregrgre')' at line 1

Its not noticing the table name.

```
<select title='Table' id='Table'>
  <option value="Her_blog">Private</option> <!-- CHANGE SO IS SET BY SESSION COOKIE-->
  <option value="Public_blog">Public</option>
</select>
<br><br>
```

---

### Post by saj0577 on 2008-05-17
Changed it to $Table = "Her_blog";

and it worked.

So its a problem with the option menu on the form i belive.

Saj

---

### Post by johnl on 2008-05-17
I suggest you use the mysqli interface and [prepared statements](http://php.oregonstate.edu/manual/en/mysqli.prepare.php) instead of the way you are doing it now, which is vulnerable to SQL injection.

ie,

$_POST['content'] == "hello'); DROP DATABASE `yourdb`"

PHP magic quotes (if turned on) may prevent this, but I wouldn't rely on it.

---

### Post by saj0577 on 2008-05-17
Okay thanks alot. Il look into it.

Saj

---

### Post by saj0577 on 2008-05-17
If anyone write it with comments on it I would be real greatful as those pages are usful but only to a certain extent.

Thanks
Saj

---

### Post by deuce868 on 2008-05-18
never ever ever ever use $_POST, $_GET, $_REQUEST directly in an sql statement or anything else for that matter. 

[http://www.google.com/search?q=sql+injection](http://www.google.com/search?q=sql+injection)

---

### Post by bvanaerde on 2008-05-18
Please look into this PHP function: [mysql_real_escape_string]("http://www.php.net/mysql_real_escape_string")

---

### Post by saj0577 on 2008-05-18
Im gonig to have a go at writing it and then if guys could check over it that would be great.

Thanks
Saj

---

### Post by saj0577 on 2008-05-21
I just cant seem to get it to work properly. :( 
Could someone create it and comment it all please. If so i would be so greatful.

Saj

---

### Post by Thirtysixway on 2008-05-21
I suggest keeping this PHP file in your root directory.  You can include it on any webpage you need, and it has many different useful sanitize functions.

[http://www.phpbuilder.com/columns/sanitize_inc_php.txt](http://www.phpbuilder.com/columns/sanitize_inc_php.txt)

```

// Function list:
// sanitize_paranoid_string($string) -- input string, returns string stripped of all non 
//           alphanumeric
// sanitize_system_string($string) -- input string, returns string stripped of special
//           characters
// sanitize_sql_string($string) -- input string, returns string with slashed out quotes
// sanitize_html_string($string) -- input string, returns string with html replacements
//           for special characters
// sanitize_int($integer) -- input integer, returns ONLY the integer (no extraneous 
//           characters
// sanitize_float($float) -- input float, returns ONLY the float (no extraneous 
//           characters)

```

---

### Post by saj0577 on 2008-05-21
This will stop mysql injection?

Saj

---

### Post by dwhitney67 on 2008-05-21
> **saj0577 said:**
> I just cant seem to get it to work properly. :( 
Could someone create it and comment it all please. If so i would be so greatful.

Saj
What is it that you cannot get to work, the mysql_real_escape_string()??

Try something like:
[PHP]
$link = mysql_connect( server, userID, password, dbTable )
        OR die( mysql_error() );

$table   = mysql_real_escape_string( $_POST["table"] );
$title   = mysql_real_escape_string( $_POST["title"] );
$date    = mysql_real_escape_string( $_POST["date"] );
$content = mysql_real_escape_string( $_POST["content"] );

$query   = sprintf( "INSERT INTO %s (Title, Date, Content) VALUES ('%s', '%s', '%s')",
                    $table, $title, $date, $content );

...[/PHP]

---


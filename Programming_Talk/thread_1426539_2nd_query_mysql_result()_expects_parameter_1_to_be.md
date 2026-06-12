---
title: "2nd query: mysql_result() expects parameter 1 to be resource, boolean given"
date: 2010-03-10
forum: Programming Talk
---

### Post by mazz0 on 2010-03-10
I've written a little PHP script to get a number from a mySQL database and increment it.  I'm new(ish) to PHP and MySQL so it's probably something obvious to do with me running a second query on the same database connection, or something like that.

My first query, to get the current value, works, but my second query, to increment the value in the database, fails with this error message:

```
PHP Warning:  mysql_result() expects parameter 1 to be resource, boolean given in /var/www/increment.php on line 15

```

Here's the code I'm running:
```
<?php
	$username="root";
	$password="password";
	$database="test";
	mysql_connect(localhost,$username,$password);
	@mysql_select_db($database) or die("Unable to select database");
	
	$query = "SELECT count FROM words WHERE value = '" . $_GET['word'] . "'";
	$result = mysql_query($query);
	echo mysql_result($result,0,"count");
	$newCount =  mysql_result($result,0,"count") + 1;

	$query = "UPDATE test SET count = '$newCount' WHERE value = '" . $_GET['word'] . "'";
	$result = mysql_query($query);
	echo mysql_result($result,0,"count");
	
	mysql_close();
?>
```

Any ideas?

---

### Post by Hellkeepa on 2010-03-10
HELLo!

"UPDATE" does not return a MySQL result type, but a boolean telling whether or not the query failed. That's why you get the error message.

Also, I strongly recommend you to validate the input. The way this script is written now, anyone could run just about any query they like on your system. In addition to that, it's also open for XSS.
I've written a few posts on how to secure scripts here before, so I recommend a search through my posts for more information.

Happy codin'!

---

### Post by mazz0 on 2010-03-10
Oh yeah, I was being a bit stupid there wasn't I?

OK, now I don't get any error, but the value doesn't update in the database - any ideas?

```
<?php
	$username="root";
	$password="password";
	$database="test";
	mysql_connect('localhost',$username,$password);
	@mysql_select_db($database) or die("Unable to select database");
	$word = $_GET['word'];
	
	$query = "SELECT count FROM words WHERE value = '$word'";
	$result = mysql_query($query);
	$count =  mysql_result($result,0,"count");
	echo $count;
	$count = $count + 1;
	echo $count;

	$query = "UPDATE test SET count = '$count' WHERE value = '$word'";
	mysql_query($query);
	
	mysql_close();
?>
```

By the way, thanks for your other advice, I'll certainly address that when I've got it working as it's going to be included in a production application containing confidential data, so it needs to be secure.

---

### Post by mazz0 on 2010-03-10
Hmm, I don't need ''s round count in the SET statement do I?  What with it being an int...

Nope, that didn't fix it...

---

### Post by mazz0 on 2010-03-10
Oops.  "test" isn't the name of the table.  "words" is.

<feels stupid>

---

### Post by Hellkeepa on 2010-03-10
HELLo!

Try this, and see if it won't work a bit better:
[php]<?php

$username = "root";
$password = "password";
$database = "test";

mysql_connect ('localhost', $username, $password);
mysql_select_db ($database) or die ("Unable to select database");

// Retrieve and validate the user provided data.
$word = val_String ($_GET['word']);

// Make sure the content is escaped, to prevent SQL injections.
$query = "SELECT count FROM words WHERE value = ".quote_smart ($word);
$result = mysql_query ($query);
$count = mysql_result ($result, 0, "count");

// Same as above, only using "sprintf ()" to sturcture things a bit better.
// Also increases the hit counter before adding it to the query.
$query = "UPDATE words SET count = %d WHERE value = %s";
mysql_query (sprintf ($query, ++$count, quote_smart ($word)))
	or die (mysql_error ()); // This line is for debugging purposes only, remove from production.

?>[/php]
You'll also notice that I've added a bit of security to it, and to find the funtions I've used please following the links in this post:
[http://ubuntuforums.org/showpost.php?p=8641992&postcount=7](http://ubuntuforums.org/showpost.php?p=8641992&postcount=7)

Happy codin'!

---


---
title: "Basic PHP MySQL query..."
date: 2010-06-27
forum: Programming Talk
---

### Post by dmillerw on 2010-06-27
I'm attempting to run a basic MySQL query, but it continues to fail, and I cannot figure out why...

[PHP]$query = mysql_query("SELECT * FROM dreams WHERE OWNER='$OWNER'");[/PHP]

and OWNER is defined as $_SESSION['username']

Whenever I run it, it can't find anything, even if there are several entries that should match

---

### Post by new_tolinux on 2010-06-27
First things first.
$OWNER != $owner

Proper escaping does no harm:
[php]$query=mysql_query("SELECT * FROM `table` WHERE `field` = '".$data."';");[/php]In this case that should be:
[php]$query=mysql_query("SELECT * FROM `dreams` where `owner` = '".$owner."';");[/php]To make sure things work, try this:
[php]$query="SELECT * FROM `dreams` where `owner` = '".$owner."';";
print $query;
$result=mysql_query($query) OR die("Error: ".$query);[/php]That way you'll find out if $owner does contain any data.

---

### Post by dmillerw on 2010-06-28
I tried that, all it did was print the query, it is using the proper value for $owner though...

[PHP]<?php

session_start();

$OWNER = $_SESSION['username'];

require("include/dbsettings.php");
mysql_connect ("$host", "$user","$pass")  or die (mysql_error());
mysql_select_db ("dreamlogs");

$query="SELECT * FROM `dreams` where `owner` = '".$owner."';";
print $query;
$result=mysql_query($query) OR die("Error: ".$query);  

?>[/PHP]

Here's the code, should it help...

[IMG]http://img8.imageshack.us/img8/6236/selection008.png[/IMG]

...and a snapshot of the database...

---

### Post by dmillerw on 2010-06-28
Anybody?

---

### Post by simeon87 on 2010-06-28
> **dmillerw said:**
> I tried that, all it did was print the query, it is using the proper value for $owner though...

[PHP]<?php

session_start();

$OWNER = $_SESSION['username'];

require("include/dbsettings.php");
mysql_connect ("$host", "$user","$pass")  or die (mysql_error());
mysql_select_db ("dreamlogs");

$query="SELECT * FROM `dreams` where `owner` = '".$owner."';";
print $query;
$result=mysql_query($query) OR die("Error: ".$query);  

?>[/PHP]

"It's hard enough to find an error in your code when you're looking for it; it's even harder when you've assumed your code is error-free."

- S. McConnell

Like the previous poster said, $OWNER is not $owner: you are storing the value in $OWNER but you are using $owner.

---

### Post by new_tolinux on 2010-06-28
[php]<?php

session_start();

$owner = $_SESSION['username'];

require("include/dbsettings.php");
mysql_connect ($host, $user, $pass)  or die (mysql_error());
mysql_select_db ("dreamlogs");

$query="SELECT * FROM `dreams` where `owner` = '".$owner."';";
print $query;
$result=mysql_query($query) OR die("Query: ".$query."<BR>Error".mysql_error());  

?>[/php]This should do the trick.
If the query is currently printing this:
```
SELECT * FROM `dreams` WHERE `owner` = '';
```that means $owner isn't set.

I also replaced the part after "die()" so it will print both the query and the produced mysql error if the query fails for any reason.
Probably not something you'll really want in a live-enviroment, but very useful when you're developing.
If you use exactly the same "die()" statement everywhere, it's not that hard to have it replaced with this when you're putting it in a live enviroment:
[php]$result=mysql_query($query) OR die("An error has occured.");[/php]

---

### Post by simeon87 on 2010-06-28
> **new_tolinux said:**
> If you use exactly the same "die()" statement everywhere, it's not that hard to have it replaced with this when you're putting it in a live enviroment:
[php]$result=mysql_query($query) OR die("An error has occured.");[/php]

It's better to use a logger, I'm sure there are also some for PHP. With a logger, you can specify what type of message you're logging and what level of messages you want to be displayed (production environment, debugging, informational, etc).

---

### Post by new_tolinux on 2010-06-28
Ofcourse you can use a logger or write your own.
It's just that for debugging purposes some info on-screen is nice, because you know exactly what's going wrong in which query.
The only thing is that you don't want to display your queries when something fails in a live-enviroment. Therefore I placed a basic replacement which will stop the script and tell that there's something wrong, but doesn't give the end-user any information.

If this is working the way the OP wants, he can always write his own kind of logging system. Although I guess that that's for the future. No offense meant, but we're talking about some very basic things here that fail. First the OP should get the basics right and have some PHP/MySQL knowledge, then he can try to build something like a logging system.

---

### Post by Hellkeepa on 2010-06-28
HELLo!

I'd also like to point out that both escaping output and validating input is completely missing from this code, making it totally open for abuse by someone who wants to attack the system (or simply uses a apostrophe in their username).

Always use "mysql_real_escape_string ()" for user-generated data in an SQL-query, or other functions that force the data to adhere to a specific pattern for non-string fields. ("intval ()" for integer fields, to name one example.)
There are also user generated functions of the SQL escaping, named "quote_smart ()", which allows you to escape in a bit more flexible manner. I recommend searching out **Stadskle**'s version from [Norsk Webforum](http://www.norskwebforum.no). I've posted the link to it a couple of times before, so a look through my posts should point you to it.

Happy codin'!

---


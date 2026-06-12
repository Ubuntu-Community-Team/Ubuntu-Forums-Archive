---
title: "PHP/MySQL"
date: 2008-05-09
forum: Programming Talk
---

### Post by kingpoiuy on 2008-05-09
Greetings,

I am working on this database project.  It is going quite well right now except for the update command.  What I am doing is I have a page where the user types in the computer they want to update (this database keeps track of serial keys for my company) and then when the user clicks ok which brings up a box to select what column to update and then the new data.  

Look at this code:
```
<html>
<body>
<?php
include 'config.php';
include 'opendb.php';
include 'serialdbindex.php';

mysql_query("UPDATE main SET '$_POST[updatedropdown]' = '$_POST[updatetextform]' 
WHERE computer='$_POST[computer]'");

echo "<br>";
echo $_POST[updatedropdown];
echo "<br>";
echo $_POST[updatetextform];
echo "<br>";
echo $_POST[computer];

include 'closedb.php'
?>
</body>
<html>
```

That will display this on my webpage but update nothing:
```
Serial Database
Home
	
	
	

user
Barb
Accounting-01 
```

Anyone out there have any ideas where I went wrong?  PHP/MySQL is treating me good sofar but i'm still a noob.

Thanks!

---

### Post by rickh57 on 2008-05-09
Are you calling this from a form that's populating the various $_POST fields?

Also, you should **always** check the status of doing the various commands. Something like this:

```

$result = mysql_query("UPDATE main SET '$_POST[updatedropdown]' = '$_POST[updatetextform]' 
WHERE computer='$_POST[computer]'");
if (!$result) {
    die('Invalid query: ' . mysql_error());
}

```

---

### Post by aks44 on 2008-05-09
```
UPDATE tablename SET field='data'
```

Note the "missing" apostrophes around "field" ;)

If you really have to surround the field name with something, use backquotes:
```
`field`
```



Side comment: what you're trying to do is VEEEERRRYYYYY unsafe code (unless you triple-checked $_POST values before actually running that code)...

---

### Post by kingpoiuy on 2008-05-09
What part is unsafe?  Sofar it is a local page only and eventually I will be including user login and such.  Any way that you guys can inform me I am very grateful of.

---

### Post by kingpoiuy on 2008-05-09
wow thoes little marks make a big difference!  :mad:

---

### Post by aks44 on 2008-05-09
> **kingpoiuy said:**
> What part is unsafe?  Sofar it is a local page only and eventually I will be including user login and such.

As long as it's a local page... well, it's ok (kinda).

The thing is, when dealing with unknown clients (ie. as soon as you open your server to anyone else than YOU), you should never ever trust them.

It's so easy to manipulate the data sent to the server, it's not even funny (I use to test my web pages with plain old **telnet**, typing the HTTP queries myself).

If you include client-provided data directly in your database queries without checking them beforehand (or escaping them, see mysql_real_escape_string or something like that) your database is basically at the mercy of any client (see: SQL injections).


Bottom line: triple-check every input before using it, and escape it as soon as you can.

---

### Post by kingpoiuy on 2008-05-09
Ok, I'll look up thoes things you mentioned.  Thanks a TON!

---


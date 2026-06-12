---
title: "[SOLVED] PHP &amp;amp; MySql - mysql_num_row"
date: 2007-08-08
forum: Programming Talk
---

### Post by rock freak on 2007-08-08
Ok this is the first time this has ever happned but mysql_num_row isnt return any value of rows!!!When they are definatly in the database!!!

I will get the source code up in about half an hour or so but didnt know if any of you clever people knew about people having problems with it!!!

*Source Code to follow*

```

<?
include 'db_con.php';

$col = "email";
$val = "test";

$query = 'SELECT * FROM `users` WHERE `email`=\'$val\'';
$result = mysql_query($query);
$row = mysql_num_rows($result);
echo "Column to search:  $col";
echo '<br />';
echo "Search value: $val";
echo '<br />';
echo "Query Result: $result";
echo '<br />';
echo "Number of rows: $row";

?>

```

EDIT: Ow and the link that its hosted on knew i forgot something [It's here]("http://www.belcom.co.uk/scripts/test.php")

Cheers 
Ollie

---

### Post by smartbei on 2007-08-08
Firstly, when I go to your example page it says that 1 row was found. So you might have already found the problem. If you didn't here it is:

You have:
```

$query = 'SELECT * FROM `users` WHERE `email`=\'$val\'';

```
The problem is that a single quote doesn't evaluate internal variables. Therefore, You should change it to:
```

$query = "SELECT * FROM `users` WHERE `email`='$val'";
//And it also looks better since you don't need to escape the single quotes.

```

Keep in mind that you shold be escaping strings that you send to your database using the mysql_real_escape_string function.

---

### Post by rock freak on 2007-08-08
Cheers for the response and yes I had just spotted that as well!!

Not a clue wot i was on when i wrote that part!! o well all is well now back to the code!!

---


---
title: "mysql_fetch_array error"
date: 2006-12-20
forum: Programming Talk
---

### Post by zetsumei on 2006-12-20
I'm getting this mysql_fetch_array error in my php script and I can't figure out what it is.

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/quotes.php on line 13

> <?
//connect to mysql
//change user and password to your mySQL name and password
mysql_connect("localhost","root","************"); 
	
//select which database you want to edit
mysql_select_db("otaku_quotes"); 

//select the table
$result = mysql_query("select * from quotes");

//grab all the content
while($r=mysql_fetch_array($result))
{	
   //the format is $variable = $r["nameofmysqlcolumn"];
   //modify these to match your mysql table columns
  
   $title=$r["title"];
   $message=$r["message"];
   $who=$r["who"];
   
   //display the row
   echo "<div class='quote'>$message</div>
	<div class='quote_author'>$who</div>";
}
?>


---

### Post by invalid on 2006-12-20
Try```
$result = mysql_query("select * from `quotes`");
```

---

### Post by zetsumei on 2006-12-20
that didnt work...i still get the error

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/quotes.php on line 13

---

### Post by invalid on 2006-12-20
Hm.. are you sure the table is populated?
Try this and see what you get```
echo mysql_num_rows($result);
```
Also, try changing to this:```
$conn = mysql_connect("localhost","root","************"); 
mysql_select_db("otaku_quotes", $conn);
```

---

### Post by zetsumei on 2006-12-20
nope i added $conn = mysql_connect( ); and the $conn into the select db part and its still giving me the same error.

---

### Post by invalid on 2006-12-21
The only other thing I can suggest are a series of debug statements```
$conn = mysql_connect("localhost","root","************");
if (!$conn) {
   die('mysql_connect error : ' . mysql_error());
}

//select which database you want to edit
$db = mysql_select_db("otaku_quotes", $conn);
if (!$db) {
   die('mysql_select_db error : ' . mysql_error());
}

//select the table
$result = mysql_query("select * from `quotes`") or die('mysql_query error : ' . mysql_error());
```

---

### Post by zetsumei on 2006-12-21
I fixed that last error, I had a o instead of 0...But now it just says $random_row instead of pulling the quote from the db

> $random_row

> <?
$cnx = mysql_connect("localhost","root","**************");
mysql_select_db("otaku_quotes", $cnx);

$sql = mysql_query("select * from quotes") or die (mysql_error());

while($row = mysql_fetch_array($sql)) {
	$row_array[] = $row['message'];
}

mysql_close($cnx);

$random_row = $row_array[rand(0, count($row_array) -1)];
echo '<div class="quotes">$random_row</div>';
?>


---

### Post by invalid on 2006-12-21
I think you mean for 'o' to be '0'.

---

### Post by zetsumei on 2006-12-21
i noticed that I edited my last post with what happens now -_-, sigh php/mysql hates me -_-

---

### Post by invalid on 2006-12-21
> **zetsumei said:**
> But now it just says $random_row instead of pulling the quote from the db

Change ```
echo '<div class="quotes">$random_row</div>';
```to```
echo "<div class=\"quotes\">$random_row</div>";
```

---

### Post by zetsumei on 2006-12-21
Finally It Works

thanks for the help

---


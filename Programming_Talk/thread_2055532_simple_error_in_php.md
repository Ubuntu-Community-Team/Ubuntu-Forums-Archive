---
title: "simple error in php"
date: 2012-09-09
forum: Programming Talk
---

### Post by sid0972 on 2012-09-09
hello

i have the following php and html scripts

```
<body>
<?php	
	$author=trim($_POST['author']);
	$title=trim($_POST['title']);
	$isbn=trim($_POST['isbn']);
	$price=$_POST['price'];
	
	if(!$author||!$title||!$isbn||!$price)
	{
		echo "values not properly filled<br> go do it again\n";
		exit;
	}
	
	if(!get_magic_quotes_gpc())
	{
		$author=addslashes($author);
		$isbn=addslashes($isbn);
		$price=doubleeval($price);
		$title=addslashes($title);
	}
	
	@ $db=new mysqli('localhost','root','my_password','books');
	if(mysqli_connect_errno())
	{
		echo "Could not connect to database, please try again later\n";
		exit;
	}
	
	$query="insert into books values('".$isbn."','".$author."','".$title."','".$price."')";
	$result=$db->query($query);
	if($result)
	{
		echo $db->affected_rows." entries inserted into database<br>";
	}
	else
	{
		echo "entry unsuccessful\n";
	}
	$db->close();
		?>

```


HTML script

```

<body>
<h1>Entry of a new book</h1>	
<form action="insert.php" method="post">
<label>Name:<input type="text" size="10" name="title"></label><br>
<label>ISBN<input type="text" size="10" name="isbn"></label><br>
<label>Author<input type="text" size="10" name="author"></label><br>
<label>price:<input type="text" size="10" name="price"></label><br>

<input type="submit" value="GO!!!"/><br>
<input type="reset" value="again!"/><br>
</form>
</body>

```


problem is that when i click on submit, it goes to insert.php, and shows a blank screen, nothing else

either it should say entries added, or should say unsuccessful, but nothing comes.

mysql table name is books, database name is books, and table is in the following order

ISBN, AUTHOR, TITLE, PRICE

what have i done wrong here?

---

### Post by snip3r8 on 2012-09-09
Are you using any sort of debugging for your php?  if you havent got debugging enabled and there are errors in your code , the page will display nothing. Try using something like netbeans with xdebug.

---

### Post by d3v1150m471c on 2012-09-09
[html]<form action="insert.php" method="post">[/html]

is your script supposed to forward your POST request to yoursite.com/insert.php ?

edit:
  you may also want to try using something like socat or telnet to send the POST data
  to see if it's not forming a readable page for a browser.

---

### Post by sid0972 on 2012-09-10
found the culprit

```
$price=doubleeval($price);
```

it should be doubleval, not doubleeval
thanks everyone for looking

---


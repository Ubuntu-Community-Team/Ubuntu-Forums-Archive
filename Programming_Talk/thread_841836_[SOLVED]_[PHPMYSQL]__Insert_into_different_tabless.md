---
title: "[SOLVED] [PHP/MYSQL]  Insert into different tables/same html form"
date: 2008-06-26
forum: Programming Talk
---

### Post by saj0577 on 2008-06-26
Hey,

I have a a html form and I want to use the same form for a few tables as all the tables require the same information.

What is the safest and securest way of using the same html form and being able to submit the data in it into different mysql tables chosen by the user(one table at a time).

Saj

---

### Post by LaRoza on 2008-06-26
> **saj0577 said:**
> Hey,

I have a a html form and I want to use the same form for a few tables as all the tables require the same information.

What is the safest and securest way of using the same html form and being able to submit the data in it into different mysql tables chosen by the user(one table at a time).

Saj

Just follow the standard safe practices. What out for injection and other code.

Having duplicate data in the tables indicates something is possibly not normalized.

---

### Post by jpeddicord on 2008-06-26
The only thing you really need to worry about, aside from SQL injection, is probably the way you prompt the user for a table. You can probably accomplish this with a simple <select> menu, though you will want to make sure that the table selected is "allowed" to prevent any hacks or bad tables being selected.

[PHP]$allowed_tables = array('table1', 'table2', 'table3');

if(in_array($_POST['selected_table'], $allowed_tables)){
    //content good, insert it into the table
}else{
    //possible tainted data, discard it and return an error
}[/PHP]

As always, be sure to escape any data before letting it into the database.

[PHP]$safe_data = mysql_real_escape_string($_POST['form_field1']);[/PHP]

---

### Post by saj0577 on 2008-06-26
create.php
[PHP]<html>
 <form action="create_proc.php" method="post">
 	<label for="Title">Title</label>
 	<input type="text" id="Title"></input>
	<label for="Table">Table</label>
 	<input type="text" id="Table"></input>
 	<INPUT type="submit" value="Send">
 </form>
[/PHP]


create_proc
[PHP]<?PHP

$db = mysql_connect('localhost' ,'username','password');
mysql_select_db('qwerty');

$allowed_tables = array('Her_Blog', 'table2', 'table3');
$safe_title = mysql_real_escape_string($_POST['Title']);  
$safe_table = mysql_real_escape_string($_POST['Table']);  

if(in_array($safe_table, $allowed_tables)){
    //content good, insert it into the table
  

$query=("INSERT INTO $safe_table (Title, Date, Content)
VALUES ('$safe_title', 'dedw', 'dwdwdw')");

if (!mysql_query($query))
  {
  die('Error: ' . mysql_error());
  }
echo "The New Blog Has Been Added Successfully!";



    
    
    
}else{
    //possible tainted data, discard it and return an error
}  
?>
[/PHP]

---

### Post by jpeddicord on 2008-06-26
[QUOTE=saj0577;5269864]create.php
```
<html>
 <form action="create_proc.php" method="post">
 	<label for="Title">Title</label>
 	<input type="text" id="Title"></input>
	<label for="Table">Table</label>
 	<input type="text" id="Table"></input>
 	<INPUT type="submit" value="Send">
 </form>

```

There's your problem. :)

Your <input> fields have no name attribute. (Also, they are single-tagged, no need to close.) Try this:

```

 <form action="create_proc.php" method="post">
 	<label for="Title">Title</label>
 	<input type="text" id="Title" name="Title" />
	<label for="Table">Table</label>
 	<input type="text" id="Table" name="Table" />
 	<INPUT type="submit" value="Send">
 </form>

```

---


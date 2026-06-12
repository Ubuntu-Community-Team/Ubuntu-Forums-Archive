---
title: "PHP/MySQL"
date: 2008-05-02
forum: Programming Talk
---

### Post by kingpoiuy on 2008-05-02
Ok, so I've been trying to get a useful database webpage up and running.  I am using PHP & MySQL. I know a little bit about php but haven't been using it for a long time. I have one webpage with checkboxes and I want it to only display the selected colums when I click the button.

Anyone know why the following displays a blank table?

Here is the php/mysql page:
```
<?php
include 'config.php';
include 'opendb.php';
include 'serialdbindex.php';

$query = "SELECT '$_POST[computer]','$_POST[user]','$_POST[windows]',
'$_POST[office]','$_POST[antivirus]','$_POST[description]' FROM main" ;

$result = mysql_query($query) or die('Error, query failed');

echo "<table border='1' align='center'>
<tr>
	<th>Computer</th>
	<th>User</th>
	<th>Windows</th>
	<th>Office</th>
	<th>Anti-Virus</th>
	<th>Description</th>
</tr>";

while($row = mysql_fetch_array($result))
	{
	echo "<tr>";
	echo "<td>" . $row['computer'] . "</td>";
	echo "<td>" . $row['user'] . "</td>";
	echo "<td>" . $row['windows'] . "</td>";
	echo "<td>" . $row['office'] . "</td>";
	echo "<td>" . $row['antivirus'] . "</td>";
	echo "<td>" . $row['description'] . "</td>";
	echo "</tr>";
	}
echo "</table>";

include 'closedb.php';
?>
```

Here is the webpage to call for it:
```
<html>
<body>
<?php
include 'serialdbindex.php'
?>
<table align='center'>

<form  action="viewtable.php" method="post" >
<tr>
	<td>
	<input type="checkbox" name="computer" >
	Computer
	</td>
</tr>


<form  action="viewtable.php" method="post" >
<tr>
	<td>
	<input type="checkbox" name="user" >
	User
	</td>
</tr>


<form  action="viewtable.php" method="post" >
<tr>
	<td>
	<input type="checkbox" name="windows" >
	Windows
	</td>
</tr>


<form  action="viewtable.php" method="post" >
<tr>
	<td>
	<input type="checkbox" name="office" >
	Office
	</td>
</tr>


<form  action="viewtable.php" method="post" >
<tr>
	<td>
	<input type="checkbox" name="antivirus" >
	Anti-Virus
	</td>
</tr>

<tr>
	<td>
	</td>
	<td>
	<input type="submit" >
	</td>
</tr>
</form>


</body>
</html>
```

I have made this page which just display's everything and it works fine:
```
<?php
include 'config.php';
include 'opendb.php';
include 'serialdbindex.php';

$query = "SELECT * FROM main" ;

$result = mysql_query($query) or die('Error, query failed');

echo "<table border='1' align='center'>
<tr>
	<th>Computer</th>
	<th>User</th>
	<th>Windows</th>
	<th>Office</th>
	<th>Anti-Virus</th>
	<th>Description</th>
</tr>";
while($row = mysql_fetch_array($result))

	{   
	echo "<tr>";
	echo "<td>" . $row['computer'] . "</td>";
	echo "<td>" . $row['user'] . "</td>";
	echo "<td>" . $row['windows'] . "</td>";
	echo "<td>" . $row['office'] . "</td>";
	echo "<td>" . $row['antivirus'] . "</td>";
	echo "<td>" . $row['description'] . "</td>";
	} 
echo "</table>";

include 'closedb.php';


?>
```

Any ideas?  I've looked around at alot of tutorials and varous pages but can't seem to find the solution.

Thanks!

---

### Post by DrMega on 2008-05-02
In your main page, I can't see where you open the db.

Have you configured PHP to report errors to the client (there is an option for this, usually switched off on production servers and on on development servers but I can't remember what the option is called).

The PHP script may be failing at the first hurdle and just not reporting as such.

---

### Post by kingpoiuy on 2008-05-02
Thanks for the reply

I open it with:
```

include 'config.php';
include 'opendb.php';

```

I close it with:
```

include 'closedb.php';

```

---

### Post by DrMega on 2008-05-02
I can see the includes in the page you have working, but not the one you're having problems with.

EDIT: Sorry, I see, the one without the includes is calling the one with. Let's take a closer look.

---

### Post by DrMega on 2008-05-02
After setting $query to be your SQL string, but before you try to run it, can you insert the following line and then run the page and see what comes out:

```

echo "<pre>";
echo $query;
echo "</pre>";

```

---

### Post by kingpoiuy on 2008-05-02
This is what I get....

I'm not sure where it is getting the 'on'

Hrmmm

```
Serial Database
Home
	
	


SELECT 'on','on','on',
'on','on','' FROM main

Computer 	User 	Windows 	Office 	Anti-Virus 	Description
					
					
		
```

---

### Post by DrMega on 2008-05-02
> **kingpoiuy said:**
> This is what I get....

I'm not sure where it is getting the 'on'

Hrmmm

```
Serial Database
Home
	
	


SELECT 'on','on','on',
'on','on','' FROM main

Computer 	User 	Windows 	Office 	Anti-Virus 	Description
					
					
		
```

I see it. Your form is full of check boxes, presumably for the fields you want to include. $_POST[*form_field_name*] gives you the values of the field (ie "on"), not its name.

I would build up the query something like this:

```

$query = "select ";

if($_POST['computer'] == 'on')
{
  $query .= "computer, ";
}
if($_POST['User'] == 'on')
{
  $query .= "user, ";
}

...so on..

$query .= "from main";

```

Now here's the thing, that still won't work directly. You'll end up with a surplus comma at the end of your field list. You can chop it off with substring() just before the final concantenation of the "from main".

---

### Post by kingpoiuy on 2008-05-02
Very nice.  That makes sense and thank you for the help! :)

---

### Post by DrMega on 2008-05-02
You're welcome.

---

### Post by kingpoiuy on 2008-05-02
Ok, so the database is doing alot better but I have this really strange thing going on now... I've been straining myself to find the bug but I have failed and it's about time to go home so I thought I would throw it up here and see if anyone is interested in taking a look at it for me.

Here is the code I ended up with in the end:
```

<?php
include 'config.php';
include 'opendb.php';
include 'serialdbindex.php';

$query = "SELECT ";


echo "<table border='1' align='center'>";
echo "<tr>";
echo "<td><b>Computer</b></td>";
if($_POST['user'] == 'on')
	{
	$query .= "user, ";
	echo "<td><b>User</b></td>";
	}
if($_POST['windows'] == 'on')
	{
	$query .= "windows, ";
	echo "<td><b>Windows</b></td>";
	}
if($_POST['office'] == 'on')
	{
	$query .= "office, ";
	echo "<td><b>Office</b></td>";
	}
if($_POST['antivirus'] == 'on')
	{
	$query .= "antivirus, ";
	echo "<td><b>Anti-Virus</b></td>";
	}
if($_POST['description'] == 'on')
	{
	$query .= "description, ";
	echo "<td><b>Description</b></td>";
	}
echo "</tr>";

$query .= "computer FROM main ORDER BY computer";
$result = mysql_query($query) or die('Error, query failed');

while($row = mysql_fetch_array($result))
	{
	echo "<tr>";
	echo "<td>" . $row['computer'] . "</td>";
	echo "<td>" . $row['user'] . "</td>";
	echo "<td>" . $row['windows'] . "</td>";
	echo "<td>" . $row['office'] . "</td>";
	echo "<td>" . $row['antivirus'] . "</td>";
	echo "<td>" . $row['description'] . "</td>";
	echo "</tr>";
	}
echo "</table>";
/*
echo "<pre>";
echo $query;
echo "</pre>";
*/
include 'closedb.php';
?>

```

it works like a charm but for some reason in the table after the 'user' column there seems to be a blank column...

I can't see any extra <td> or anything like that anywhere.  It just baffles me!

If this isn't enough info let me know and I can do a screen shot or something I just haven't yet because this database contains serial numbers so I would have to fuz them all out in order to post it.

Thanks!

---


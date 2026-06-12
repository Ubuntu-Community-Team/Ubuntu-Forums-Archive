---
title: "php search form"
date: 2008-08-06
forum: Programming Talk
---

### Post by Mia_tech on 2008-08-06
I've wanted to create a search form and the search will be against table called articles with columns: title, date, info, url. This table will store information about the articles in a website, I've came up with my a very simple php script, but the problem is that it doesn't matter what you put into the search box it will return the entire table and the part of the problem is in the sql statement, which is not doing a filtering I'm using "SELECT * FROM articles" and I know I should put some sort of "WHERE * LIKE *" in the query, I just can't find the php code for it, anyway here's the php code
```
<?php
//open connection
$conn = mysql_connect("localhost", "root", "password") or die(mysql_error());
//select database
mysql_select_db("test", $conn);
//the sql statement
$sql = "SELECT * FROM articles";
//execute the statement
$data = mysql_query($sql, $conn) or die(mysql_error());
while ($result = mysql_fetch_array($data)) {
    //giving names to the fields
    $title = $result['title'];
    $date = $result['date'];
    $info = $result['info'];
    $url = $result['url'];
    //put the results on the screen
    echo "<b>$title</b>";
    echo " ";
    echo "<b>$date</b><br>";
    echo "$info<br>";
    echo "$url<br>";
}
?> 
```
here is the search form
[HTML]<h2>Search</h2> <form name="search" method="post" action="search1.php"> Seach for: <input type="text" name="find" /> <input type="submit" name="search" value="Search" /> </form>[/HTML]
any help or suggestion on how to make this work would be appreciated 
thanks

---

### Post by scragar on 2008-08-06
```
//....
mysql_select_db("test", $conn);


$input = $_POST['find'];

if(!get_magic_quotes_gpc()){// magic quotes off
  $input = addslashes($input);
};

$arSearch = preg_split("/\b/", $input);// get an array of terms

$sql = "SELECT * FROM articles WHERE 1";// make it default to finding all

foreach($arSearch as $tmp){
  $tmp .= " AND (title LIKE '%{$tmp}%' OR contents LIKE '%{$tmp}%')";
};


$data = mysql_query($sql, $conn) or die(mysql_error());
while ($result = mysql_fetch_array($data)) {

//...

```

---

### Post by Mia_tech on 2008-08-06
thanks for the code...much appreciated, do you mind to put explain the code as I'm not an experienced of a php programmer


thanks

---

### Post by scragar on 2008-08-06
```
$input = $_POST['find'];// just store the users input

if(!get_magic_quotes_gpc()){// magic quotes is the same as addslashes
                            // so we just make sure that if they are turned off
                            // (remember, ! means NOT) we just add slashes
  $input = addslashes($input);
};


$arSearch = preg_split("/\b/", $input);// preg_split breaks a string into an array
                                       // since it takes a regexp I use \b
                                       // which matches the gaps between any words

$sql = "SELECT * FROM articles WHERE 1";// make it default to finding all
                                        // remember, 1 always evaluates to true

foreach($arSearch as $tmp){// loop through the array and store each value as tmp
  $sql .= " AND (title LIKE '%{$tmp}%' OR contents LIKE '%{$tmp}%')";
// add a string to the end of the sql, which makes it something like:
// SELECT * FROM... WHERE 1 AND (title LIKE '%term%' OR contents LIKE '%term%')
// this means it will match as long as all terms appear atleast once in either the
// title or contents
};

```

---

### Post by Mia_tech on 2008-08-06
well because I quite didn't find that code very simple.. something that I wanted to stick to, I kept searching and I found that my original code wasn't too far from what I wanted, so I finished it and test it a bit and I think is holding up, anyway here's the final code, like I said is very simple (for beginners )
[PHP]<?php
$input = $_POST['find'];
//If they did not enter a search term we give them an error
if ($input == "")
{
echo "<p><h3>You forgot to enter a search term!</h3>";
exit;
} 
//open connection
$conn = mysql_connect("localhost", "root", "password") or die(mysql_error());
//select database
mysql_select_db("test", $conn);
//the sql statement
$sql = "SELECT * FROM articles WHERE info LIKE '%$input%'";
//execute the statement
$data = mysql_query($sql, $conn) or die(mysql_error());
while ($result = mysql_fetch_array($data)) {
	//giving names to the fields
	$title = $result['title'];
	$date = $result['date'];
	$info = $result['info'];
	$url = $result['url'];
	//put the results on the screen
	echo "<b>$title</b>";
	echo " ";
	echo "<b>$date</b><br>";
	echo "$info<br>";
	echo "$url<br>";
}
//This counts the number or results - and if there wasn't any it gives them a little message explaining that
$anymatches=mysql_num_rows($data);
if ($anymatches == 0)
{
echo "<h3>Sorry, but we can not find an entry to match your query!</h3><br>";
} 
//And we remind them what they searched for
echo "<b>You searched for:</b> " .$input; 
?>[/PHP]

enjoy

thanks

---

### Post by Mia_tech on 2008-08-06
ok I take that back, actually there's something I would like to add, and is in the output page the url is not in the form of a link, how could I get that to display as a link in php?...here's what the output looks

Pentesting MS SQL Server with SQLat, and Cain. 2008-08-03
Well for this tutorial I will be pentesting MS SQL Server with SQLat, Freetds, and Cain. Database store and provide access to information and information is power. Sensitive data such as bank account numbers, credit reports, and lots of other important
[http://localhost/pentesting_mssql.html](http://localhost/pentesting_mssql.html)
You searched for: sql

---

### Post by Mia_tech on 2008-08-06
never mind with a little bit of thinking got that too...

[PHP]echo "<a href=$url>$url</a>";[/PHP]


thanks

---

### Post by Reiger on 2008-08-06
If you search for ordinary data; you should (good practice) use a $_GET superglobal instead of $_POST. Requires the method in your input form is set to "get" (instead of "post").

The benefit will be that you can bookmark a site URL with a GET String appended to it.

So you may have something like:

.../search.php?find=history%20of%20the%20zipper

(Someone searched your DB for "history of the zipper"...)

---

### Post by Mia_tech on 2008-08-06
> **Reiger said:**
> If you search for ordinary data; you should (good practice) use a $_GET superglobal instead of $_POST. Requires the method in your input form is set to "get" (instead of "post").

The benefit will be that you can bookmark a site URL with a GET String appended to it.

So you may have something like:

.../search.php?find=history%20of%20the%20zipper

(Someone searched your DB for "history of the zipper"...)

well I've read that the use of GET method is not very secure as you can see the actual request on the address bar as you noted above

---


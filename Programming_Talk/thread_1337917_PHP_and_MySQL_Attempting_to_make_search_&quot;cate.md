---
title: "PHP and MySQL: Attempting to make search &quot;categories&quot;"
date: 2009-11-25
forum: Programming Talk
---

### Post by dmillerw on 2009-11-25
So I've got a basic search engine type code, and I'm attempting to have it search through different categories depending on which radio button is selected

[PHP]<form action="search.php" method="post">&nbsp;<input name="term" type="text"><input name="submit" value="Search Database" type="submit"><br><input type="radio" name=cat value="School" >School

<input type="radio" name=cat value="Facebook">Facebook

<input type="radio" name=cat value="MySpace">MySpace

<input type="radio" name=cat value="Other">Other
<input type="radio" name=cat value="All" >All</form><br><br>

<b><a href="index.html" target="_top">Back</a></b>
<br>
---
<br>
<?php
mysql_connect ("localhost", "root","pwordhere")  or die (mysql_error());
mysql_select_db ("pwordlist");

$term = $_POST['term'];
$cat = $_POST['cat'];

$sql = mysql_query("select * from PWordTable where FName like '%$term%' or LName like '%$term%' or UName like '%$term%' or StuID like '%$term%' AND Cat IS '%$cat%' ORDER BY LName ");

while($row = mysql_fetch_array($sql)){
        print "<a href = 'options.php?id=".$row['ID']."'>".$row['LName']."</a>";
        print ", <a href = 'options.php?id=".$row['ID']."'>".$row['FName']."</a>";
        echo '<br/>';
}
?>
---
<br>
<b><a href="index.php" target="_top">Back</a></b>
<br>
---
<br>
<b>
Can't find the entry you're looking for? <a target="_top" href="form.php">Add</a> a new one
</b>
[/PHP]

Problem is, it doesn't seem to take the Radio button value into consideration, just searches like normal

Any input?

---

### Post by BenAshton24 on 2009-11-25
[PHP]$query_text = sprintf("SELECT * FROM PWordTable WHERE FName like '%%s%' OR LName like '%%s%' OR Uname like '%%s%' OR StuID like '%%s%' AND Cat='%%s%'", mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($cat));

$sql = mysql_query($query_text) or die(mysql_error());[/PHP]

---

### Post by dmillerw on 2009-11-25
Got an error

> Notice: Undefined variable: cat in /opt/lampp/htdocs/search.php on line 20
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '%sR Uname like '%sR StuID like '%sND Cat='%s' at line 1

---

### Post by BenAshton24 on 2009-11-25
[PHP]

$query_text = sprintf("SELECT * FROM PWordTable WHERE FName like '%%%s%%' OR LName like '%%%s%%' OR Uname like '%%%s%%' OR StuID like '%%%s%%' AND Cat='%%%s%%'", mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($term), mysql_real_escape_string($cat));

$sql = mysql_query($query_text) or die(mysql_error());[/PHP]

sorry, I forgot to double up on the percents :P $cat shouldn't be undefined if you still have the line "$cat = $_POST['cat'];". Sorry, if you get any more errors I don't have time to double check it as i'm sorta rushing this response... got quite a lot of work to do and it's getting late :(

---

### Post by dmillerw on 2009-11-25
Now its just not searching through categories again, just displaying everything that fits the search terms...

Odd

---

### Post by dmillerw on 2009-11-26
Anyone?

---

### Post by CyberJack on 2009-11-26
I guess the main problem is with the OR's and the AND in the query. If one of the OR's is matched the result is shown.

A second thing is the $cat value. Must it be a like in your query? (do you have cat names like Schoolllll) or do the values from the radio buttons match the names in the database?

Can you try the following:
This code seperates the group of OR and the one AND statement. It also uses a fixed name for the Cat field.

[PHP]
$term = $_POST['term'];
$cat  = $_POST['cat'];

$sql = sprintf("SELECT *
                FROM PWordTable
				WHERE (FName LIKE '%%%s%%' OR LName LIKE '%%%s%%' OR UName LIKE '%%%s%%' OR StuID LIKE '%%%s%%')
				AND Cat = '%s'
				ORDER BY LName ASC", mysql_real_escape_string($term),
				                     mysql_real_escape_string($term),
				                     mysql_real_escape_string($term),
				                     mysql_real_escape_string($term),
									 mysql_real_escape_string($cat));
$result = mysql_query( $sql );
if( $result )
{
	while( $row = mysql_fetch_array($result, MYSQL_ASSOC) )
	{
		echo '<a href="options.php?id='. $row['ID'] .'">'. $row['LName'] .'</a>';
        echo ', <a href="options.php?id='. $row['ID'] .'">'. $row['FName'] .'</a>';
        echo '<br/>';
	}
}
[/PHP]

---

### Post by dmillerw on 2009-11-26
Thanks, that did it, one question though, anyway to make the "All" option, actually search through all the categories?

---

### Post by CyberJack on 2009-11-26
You will have to split-up the query to make the "All" option work.
When "All" is selected, just don't insert the "AND Cat = '%s' " part into the query. Like so:

[PHP]
$term = $_POST['term'];
$cat  = $_POST['cat'];

// Build query (first part)
$sql = sprintf("SELECT *
                FROM PWordTable
                WHERE (FName LIKE '%%%s%%'
                       OR LName LIKE '%%%s%%'
                       OR UName LIKE '%%%s%%'
                       OR StuID LIKE '%%%s%%')", mysql_real_escape_string($term),
                                                 mysql_real_escape_string($term),
                                                 mysql_real_escape_string($term),
                                                 mysql_real_escape_string($term));

// Only add the where of the not 'All' option is selected
if( 'All' != $cat )
  $sql .= sprintf(" AND Cat = '%s'", mysql_real_escape_string($cat));

// Add the order by to the query
$sql .= " ORDER BY LName ASC";
                               
// Done building... execute the query     
$result = mysql_query( $sql );
if( $result )
{
    while( $row = mysql_fetch_array($result, MYSQL_ASSOC) )
    {
        echo '<a href="options.php?id='. $row['ID'] .'">'. $row['LName'] .'</a>';
        echo ', <a href="options.php?id='. $row['ID'] .'">'. $row['FName'] .'</a>';
        echo '<br/>';
    }
}  
[/PHP]

---


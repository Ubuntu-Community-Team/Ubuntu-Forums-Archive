---
title: "PHP Help"
date: 2009-11-17
forum: Programming Talk
---

### Post by dmillerw on 2009-11-17
[/CODE]

(search.php)
```
<?php
mysql_connect ("localhost", "root","pwordhere")  or die (mysql_error());
mysql_select_db ("pwordlist");

$term = $_POST['term'];

$sql = mysql_query("select * from PWordTable where FName like '%$term%' or LName like '%$term%' or UName like '%$term%' or StuID like '%$term%' ");

while ($row = mysql_fetch_array($sql))
{
	echo 'ID: '.$row['ID'];	
	echo '<br/> First Name: '.$row['FName'];
	echo '<br/> Last Name: '.$row['LName'];
	echo '<br/> Student ID: '.$row['StuID'];
	echo '<br/> Username: '.$row['UName'];
	echo '<br/><br/>';
	}

?>

<FORM><INPUT TYPE="button" VALUE="Back" onClick="history.go(-1);return true;"> </FORM>






```

So I've got this code, and as you can see, it echos the ID for each row listed, what I want to do is have the FName link to a page (most likely options.php?ID) but I'm not sure how to fetch the ID from the database for that particular row, and create a link using FName, any ideas?

---

### Post by qalimas on 2009-11-17
Looks like the line ```
$sql = mysql_query("select * from pwordlist-table where FName like '%$term%' or LName like '%$term%' ");
``` is returning either a true or false.  What happens if you add ```
echo $sql;
``` before the where claus?

---

### Post by dmillerw on 2009-11-18
Thanks, that solved that problem, new problem in OP

---

### Post by korvirlol on 2009-11-18
[PHP]while($row = mysql_fetch_array($sql)){
     print "<a href = 'options.php?id=".$row['FName']."'>".$row['FName']."</a>";
}[/PHP]

---

### Post by dmillerw on 2009-11-18
What I meant was having a link such as options.php?ID=(the id number corrisponding to the row) and have it create a hyperlink on the FName, basically, the First name is the link

Sorry if I'm not explaining well, I'm sick and tired...

EDIT: Ah, nevermind, I see what the code does

---

### Post by dmillerw on 2009-11-18
OK, so I've got the custom options.php for each entry, now, how would I filter it out so it only outputs the ID of the current user, and inputs THAT into a Delete function

Basically, I want there to be a delete option for the particular user under the options.php

---

### Post by korvirlol on 2009-11-18
So what ouputs the Id of the user?

Using the example i linked above to options.php, you can access the ID of each user by clicking on the appropriate link generated.

As in, if you click on the appropriate link for a specific user, you can access that Id in options.php by: $_GET['id'].

Then you can use this id in your delete clause.

Be very careful with directly inserting content from POST or GET arrays into your database though. Read: SQL injection.

Im not sure what you mean by custom options.php... if you have hardcoded in user-ids, this is definitely the wrong way to go.

---

### Post by dmillerw on 2009-11-18
Sorry to be a bother, but I'm not that experienced with PHP and MySQL.

So, I'm going to post what exactly I'm trying to do, and see if anyone can walk me through it.

So I've got a search box, which can search for the First or last name, student ID or user name.

The search result has a link to a "options.php" with a predefined ID at the end.

What I'd like to have on the options.php page is two options, one for edit, and one for delete.

This is where I'm struggling, I've tried numerous things, to no avail.

Anyone willing to help?

---

### Post by MonoDeem on 2009-11-18
```
1. options.php?id=5&action=edit
2. options.php?id=5&action=delete

```


[LIST=1]
[*]Fetch data again and add values to the form ( submit it to wherever you want and update the database ).
[*]Create a confirmation dialog and delete the entry if it returned [COLOR=Green]true[/COLOR].
[/LIST]

---

### Post by dmillerw on 2009-11-18
I know that bit, what I'm having trouble with is the actual coding required.

---

### Post by MonoDeem on 2009-11-18
Here's an example ( of course, you still need to finish it ):

[PHP]$id = $_GET['id'];
$action = $_GET['action'];

switch ($action) {
    case 'delete':
        $query = mysql_query("DELETE FROM table WHERE id='$id'") or die(mysql_error());
        echo "Row [$id] deleted!";
        break;
    case 'edit':
        $query = mysql_query("SELECT * FROM table WHERE id='$id'") or die(mysql_error());
        echo "ID found! You may proceed with editing .. <br />";
        break;
    default:
        echo "Invalid command: " . $action . "<br />";
        exit();
}[/PHP]

---

### Post by dmillerw on 2009-11-19
OK, thanks for that

say I've got this for the mysql_query:

```
$sql = mysql_query("select * from PWordTable where FName like '%$term%' or LName like '%$term%' or UName like '%$term%' or StuID like '%$term%' ");
```

What would I set %term% to in order to compare it to a current variable

For example, the link uses the variable for the StuID, how would I use that variable to find the info for that row and have it store the ID column bit in a new variable ($id)

---

### Post by korvirlol on 2009-11-19
if the variable you want to access is in the url, you access it by:

[PHP]$_GET['index'][/PHP]

if it is in the post array you access it by:

[PHP]$_POST['index'][/PHP]

if you want to be really lazy and less secure you can acces it by:
[PHP]
$_REQUEST['index'][/PHP]

your sql statement will look like:
[PHP]
$q = mysql_query("select fields from table where attribute = '".$_GET['index']."' ");[/PHP]

---

### Post by dmillerw on 2009-11-19
```
Warning: mysql_fetch_array() expects parameter 1 to be resource, boolean given in /home/server/public_html/options.php on line 11
```

---

### Post by korvirlol on 2009-11-19
It would help if you posted the query that is failing...

I would strongly encourage you to take some online php tutorials, or buy a book about it (if you are actually serious about developing in php). While the people on this forum are knowledgeable and helpful, you cant expect them to hold your hand through your development

---

### Post by dmillerw on 2009-11-19
I see your point, and will do that, however this is pretty much the only thing thats still giving me trouble. If you would be willing to help with this last little bit, I'd love it, otherwise, thanks for your help

```
<?php
mysql_connect ("localhost", "root","pword")  or die (mysql_error());
mysql_select_db ("pwordlist");

$q = mysql_query("select fields from PWordList where attribute = '".$_GET['id']."' ");  

while($row = mysql_fetch_array($q)){
	echo 'ID: '.$row['id'];
	}

?>
```

---

### Post by korvirlol on 2009-11-19
if infact the variable in your url is labelled id then all you need to do is change "fields" to "*" in your query


fields was just an example

---

### Post by MonoDeem on 2009-11-19
> **dmillerw said:**
> I see your point, and will do that, however this is pretty much the only thing thats still giving me trouble. If you would be willing to help with this last little bit, I'd love it, otherwise, thanks for your help

```
<?php
mysql_connect ("localhost", "root","pword")  or die (mysql_error());
mysql_select_db ("pwordlist");

$q = mysql_query("select fields from PWordList where attribute = '".$_GET['id']."' ");  

while($row = mysql_fetch_array($q)){
    echo 'ID: '.$row['id'];
    }

?>
```

[PHP]$q = mysql_query("SELECT fields FROM PWordList WHERE attribute='".$_GET['id']."'") or die(mysql_error()); [/PHP]

What does it say ?

---

### Post by dmillerw on 2009-11-19
```
$q = mysql_query("SELECT ID FROM PWordTable WHERE attribute='".$_GET['id']."'") or die(mysql_error());
```

Unknown column 'attribute' in 'where clause'

EDIT: Fixed that...

---

### Post by MonoDeem on 2009-11-19
> **dmillerw said:**
> ```
$q = mysql_query("SELECT ID FROM PWordTable WHERE attribute='".$_GET['id']."'") or die(mysql_error());
```Unknown column 'attribute' in 'where clause'

EDIT: Fixed that...

Fixed .. what ?

---

### Post by dmillerw on 2009-11-19
The error, my bad.

OK, I've got most of this sorted out, except what will define the deletion.

To get to the "options.php" where the delete and eventually edit options will be, I'm using this:

```
print "<br/>First Name: <a href = 'options.php?id=".$row['ID'].$row['FName']."'>".$row['FName']."</a>";
```

Then over on the "options.php" page, I've got ```
$q = mysql_query("SELECT * FROM PWordTable WHERE ID='".$_GET['id']." AND FName='".$_GET['fname'].") or die(mysql_error());  
``` in order to echo the FName and ID to make sure its correct, problem is I'm getting this error:

```
Parse error: syntax error, unexpected T_ENCAPSED_AND_WHITESPACE, expecting T_STRING or T_VARIABLE or T_NUM_STRING in /home/server/public_html/options.php on line 12
```

I really appreciate the help, and for putting up with my n00bishness...

---

### Post by MonoDeem on 2009-11-19
[PHP]$q = mysql_query("SELECT * FROM PWordTable WHERE ID='".$_GET['id']."' AND FName='".$_GET['fname']."'") or die(mysql_error());
[/PHP]

---

### Post by korvirlol on 2009-11-19
if the code you posted is copied from your file then you need ending single quotes at the end of your variables in your query.

---

### Post by dmillerw on 2009-11-19
OK, I've got pretty much everything figured out

Seriously, thank you all for your help, I do not know of many people who put up with people like me, and I appreciate it.

:)

---


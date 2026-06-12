---
title: "need help calling up a single row with php and MySql"
date: 2010-09-25
forum: Programming Talk
---

### Post by lang79james on 2010-09-25
Right now I am just doing baby steps. The end project will be where I something like a blog to a website and be able to edit or delete an entry. 

What I got now
A admin page where I can enter a new entry and view what is posted. 

A test page where I can view what I have entered with a link to anther page where to view just one entry

After a couple of days of research I came up with this for the following pages

Main test page

[PHP]<?
include 'dbuser.php';

// Connect to the data base 
$dbc = mysqli_connect($server, $user, $pass , $db)
    or die('Error connecting to MySQL server.');

// Retrieve data base 
    //$query = "SELECT * FROM `current` WHERE 1"; 
    //$data = mysqli_query($dbc, $query);
    
    $query = "SELECT * FROM `current` ORDER BY `current`.`id` DESC LIMIT 0, 30 ";     
    $data = mysqli_query($dbc, $query);



// Loop through the array of payment data

while ($row = mysqli_fetch_array($data)) {
// Display the current news data 

  
  echo '<h3>'. $row['tittle'] . '</h3>'  ;
  echo $row['date'] . '<br />' ;
  echo $row['message'] . '<br />';
  echo 'Row ID:' . $row['id'] ;
  echo "<a href=\"del.php?del=".$row['id']."\">edit</a><br />";
 }

mysqli_close($dbc);





?>
[/PHP]

Page where i just want to view one

[PHP]<?

include 'dbuser.php';
$id = $_GET['id'];

// Connect to the data base 
$dbc = mysqli_connect($server, $user, $pass , $db)
    or die('Error connecting to MySQL server.');


// Retrieve data base 
    $query = "SELECT * FROM `current` WHERE id='$id'"; 
    $data = mysqli_query($dbc, $query);
    
    


// Loop through the array of payment data

while ($row = mysqli_fetch_array($data)) {
// Display the current news data 

  
  echo '<h3>'. $row['tittle'] . '</h3>'  ;
  echo $row['date'] . '<br />' ;
  echo $row['message'] . '<br />';
  echo 'Row ID:' . $row['id'] ;
  
 }

mysqli_close($dbc);
?>[/PHP]

What I get on the del.php page is nothing just blank. 

Now what am I doing wrong. 
Thanks for any help

---

### Post by Some Penguin on 2010-09-25
Not a PHP programmer by any means, but three things that strike me as wrong:

* 'Tittle' should probably be 'Title'.
* Your code appears vulnerable to an SQL injection attack, e.g. a request where the id is ```
';DROP TABLE current;'
``` might be bad.
* Backquotes around `current` seem unnecessary to me.  Ditto for id.  Non-MySQL-ish.

---

### Post by lang79james on 2010-09-25
Well this is far from finish and this is just get it to work. Once i am done with just getting it to work then I will work on making it more secured.

---

### Post by Pyro.699 on 2010-09-25
Check this out: [http://www.ricocheting.com/code/php/mysql-database-class-wrapper-v3](http://www.ricocheting.com/code/php/mysql-database-class-wrapper-v3)

makes executing MySQL code much simpler :) It has a ton of handy examples too

---

### Post by SeijiSensei on 2010-09-25
Give yourself a bit of help by adding some debugging information into the code like this:

```
<?

include 'dbuser.php';
$id = $_GET['id'];

echo "<h4>ID=$id</h4>";

// Connect to the data base 
$dbc = mysqli_connect($server, $user, $pass , $db)
    or die('Error connecting to MySQL server.');


// Retrieve data base 
    $query = "SELECT * FROM `current` WHERE id='$id'"; 
    $data = mysqli_query($dbc, $query);
    
    


// Loop through the array of payment data

echo "<h4>Data array has ".mysql_num_rows($data)." rows</h4>";

while ($row = mysqli_fetch_array($data)) {
// Display the current news data 

  
  echo '<h3>'. $row['tittle'] . '</h3>'  ;
  echo $row['date'] . '<br />' ;
  echo $row['message'] . '<br />';
  echo 'Row ID:' . $row['id'] ;
  
 }

mysqli_close($dbc);
?> 

```

You should see the ID and the number of rows returned when you run the script.  Are they the values you expected?  (You can turn off the debugging by putting a hash mark, "#", at the beginning of the "echo" I added lines.)

---

### Post by lang79james on 2010-09-25
SeijiSensei 

To me it seems like like on the main page is not calling the id on the del page

all i get is 

ID=

Data array has rows

---

### Post by Some Penguin on 2010-09-26
*shrug*  You should be consistent as to whether you want the parameter to be named 'ID', or 'del'.

```

echo "<a href=\"del.php?del=".$row['id']."\">edit</a><br />"; 

```

uses the latter.

---

### Post by SeijiSensei on 2010-09-26
^This

Either use 

$id=$_GET['del'];

or name the parameter "id" in the URL.

---

### Post by lang79james on 2010-09-26
> **SeijiSensei said:**
> ^This

Either use 

$id=$_GET['del'];

or name the parameter "id" in the URL.

like this :
[PHP]echo "<a href=\"del.php?id=".$row['id']."\">edit</a><br />";[/PHP]

wow what you know it works thanks all:P
know I am going to try to make some code to edit what is in the tables so i might be back later. 

The issue I was having that I am a cut and paste coder trying to learn through examples.

So just that I am learning this 

echo "<a href=\"del.php?id=".$row['id']."\">edit</a><br />";

del.php is the page I am calling 
id= is the information is sending to the next page.
".row['id'} is a more direct information so when I call $id it knows where to look in the database.

---


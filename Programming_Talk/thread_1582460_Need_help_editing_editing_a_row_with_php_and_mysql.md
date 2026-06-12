---
title: "Need help editing editing a row with php and mysql"
date: 2010-09-26
forum: Programming Talk
---

### Post by lang79james on 2010-09-26
My project is to create a page where I can update news in a journal type of environment
Things need to be done:
create database with fields - done
create page to enter data in the database - done
create page to view the entry - done
create a page to edit or delete entries - not done 

what is done on this page
Able to view the single entry - done
The form to inter new data - done but sure there is an error
code to update or replace - full of errors
code to delete entry - not done 

What I want is for every action requires the user to enter the password for the database.

Here is what I got so far.

[PHP]<table border="1" align="center" cellspacing="1" cellpadding="1">
<tr valign="top">
<td><h2>Edit to Current News</h2>

<tr valign="top">
<td>

<?

include 'dbuser.php';
  $id = $_GET['id'];
  $date = date("Y/m/d"); 
  $tittle = $_POST['tittle'];
  $message = $_POST['message'];
  $password = $_POST['password'];
  $date = date("Y/m/d"); 
  $tittle = $_POST['tittle'];
  $message = $_POST['message'];
  $password = $_POST['password'];
  $form = "
  <p>Please enter the following:</p>
  	<form method=\"post\" action=\"".$_SERVER["PHP_SELF"]."\">
	<p><strong>Title:</strong><br/>
	<input type=\"text\" name=\"tittle\" size=\"30\" maxlength=\"75\">
	</p>

	<p><strong>Your Currnet News:</strong><br/>
	<textarea name=\"message\" cols=\"40\" rows=\"3\" wrap=\"virtual\"></textarea></p>

	<p><strong>password For Site:</strong><br/>
        <p>
	<input type=\"password\" name=\"password\" size=\"30\" maxlength=\"50\">
	<input type=\"submit\" name=\"submit\" value=\"Add Entry\"></p>
	</form>";

     

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

?>

</td>

<tr valign="top">
<td>

<?php echo $form ; ?>


<?php

 

// Connect to the data base 
$dbc = mysqli_connect($server, $user, $password , $db)
    or die('Error connecting to MySQL server.');

// Writing to the data base
 $query = "UPDATE $db .`current` SET `tittle` = \'$tittle\', `message` = \'$message\' WHERE `current`.`id` = $id;";

  $result = mysqli_query($dbc, $query)
    or die('Error writing to database.');



mysqli_close($dbc);
?>
    </td>
</table>[/PHP]

Right now i am doing baby steps 
So I need help coding to edit the row.

What happens when I use the replace and update command 
I get error writing to the database

What I think is the $id is not getting called maybe?

---


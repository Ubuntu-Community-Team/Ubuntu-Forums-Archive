---
title: "Duplicate entry '0' for key 1"
date: 2007-10-18
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-18
There are several hits in Google for "Duplicate entry '0' for key 1' but none of them seem to be my problem.  The problem code is 

```

// add the new information into the database
$query="INSERT INTO wishlist (name,id,pic,link,description,type,price) VALUES ('$_POST[name]','$_POST[id]','$_POST[pic]','$_POST[link]','$_POST[description]','$_POST[type]','$_POST[price]')";
if(!mysql_db_query($dbname,$query)) die(mysql_error());
echo "success in database entry.";

echo "<br />";
echo "<a href=\"wishlistEntry.php\">Click here to return to the form page.</a>";

```

I think what is happening is that the database is trying to submit something before the submit button is pressed.  The default value for the primary key is actually 10 (change from zero during debugging).  Eventually I'd like to figure out how to auto-increment the key, but there's no reason to worry about that for now.

---

### Post by mrvertigo on 2007-10-18
are you working with a CMS if so which one, I dont see the problem in the code above but i'm admittedly tired and squinty eyed, looks like your using php is it possible that the db is referenced elcewhere on the page and somehow gaining priority over the desired command or entry?

---

### Post by DouglasAWh on 2007-10-18
> **mrvertigo said:**
> are you working with a CMS if so which one, I dont see the problem in the code above but i'm admittedly tired and squinty eyed, looks like your using php is it possible that the db is referenced elcewhere on the page and somehow gaining priority over the desired command or entry?

Definitely using PHP.  I am not using a CMS.  It's funny you should ask that, because most of the Google hits seem to involve either a Java connection or a CMS (no Java interaction either).

---

### Post by mrvertigo on 2007-10-18
first off I HAVE to point you to [http://www.ubuntuSC.com](http://www.ubuntuSC.com)
that being said you never answered if there was annother command that might be referencing your DB on that page uppon the same event

---

### Post by DouglasAWh on 2007-10-18
it appears as though you don't accept (or cannot accept) private messages, so depending on where you are in SC, you might be particularly interested in [http://www.cota-atlanta.org/](http://www.cota-atlanta.org/).  It's in Atlanta, if the URL doesn't give that away.  

As to the database connection question, I'm tired and going to bed, but here's my code.  I've been playing with the session stuff to see if I could fix the problem, but that wasn't part of the original code.

```

<?php
if($HTTP_SERVER_VARS["HTTPS"] != "on")  
{ 
   $newurl = "https://" . $_SERVER["SERVER_NAME"] . $_SERVER["REQUEST_URI"]; 
   header("location: $newurl");    
}

// Start a session, and set a key and a counter
// A session is a method of tracking state for a given 
// browser session, and allows storage of data on the server
session_start(); // create a session
session_register('session_key');      // register a session var for a key to 
                                      // track this session
                                      // this is done to help detect reloads
session_register('session_counter');  // session counter is used to track where we are in
                                      // a session
// if the session_key is not yet set, generate a random number for the key
// and set the session_counter to 0 (this situation indicates that the form
// is being loaded for the first time)
if (!$_SESSION['session_key']) {
   $_SESSION['session_key'] = rand();
   $_SESSION['counter'] = 0;
   } 

//**** External Files
// Call a file with some general functions, this file is required
require_once '../form/general_functions-1.3.php';
//**** Set some variables
$title = "Wishlist Entry";


 echo "<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Transitional//EN\"\n";
  echo "\"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd\">\n";
  echo "<html xmlns=\"http://www.w3.org/1999/xhtml\">\n";
  echo "<head><title>$title</title>\n"; 
 echo "<link href=\"wishlist.css\" rel=\"stylesheet\" type=\"text/css\" />\n";
   echo "</head>\n";
  echo "<body>\n";
  
  


// Start of the visible form
echo "<div id=\"container\">";
echo "<div id=\"maincontent\">";


$dbhost = 'nope';
$dbuser = 'nada';
$dbpass = 'right...';

$conn = mysql_connect($dbhost, $dbuser, $dbpass) or die                      ('Error connecting to mysql');

$dbname = 'sorry';
mysql_select_db($dbname);

// connect to server, database, table.
//something to think about for later
//include ("db_connect.inc");
if ($_SESSION['counter'] == 0)
{echo '<p><object><form action="'. $_SERVER["PHP_SELF"] . '" method="post" name="choices">';
// echo "<form method=\"post\" action=\"enter_it.php\">";
echo "<label for=\"alignment\">Item Name :</label> <input type=\"text\" name=\"name\" /><br />";
echo "<label for=\"alignment\">Key Number :</label> <input type=\"text\" name=\"id\" /><br />";
echo "<label for=\"alignment\">Picture URL :</label> <input type=\"text\" name=\"pic\" /><br />";
echo "<label for=\"alignment\">Page URL :</label> <input type=\"text\" name=\"link\" /><br />";
echo "<label for=\"alignment\">Description :</label> <input type=\"text\" name=\"description\" /><br />";
echo "<label for=\"alignment\">Type :</label> <input type=\"text\" name=\"type\" /><br />";
echo "<label for=\"alignment\">Price :</label> <input type=\"text\" name=\"price\" /><br />";
echo "<input type=\"submit\" name=\"submit\" value=\"submit\" />";
echo "</form></object></p>";
$_SESSION['counter'] = 1;}

echo $_SESSION['counter'];
// add the new information into the database
if ($_SESSION['counter'] != 0)

{
$query="INSERT INTO wishlist (name,id,pic,link,description,type,price) VALUES ('$_POST[name]','$_POST[id]','$_POST[pic]','$_POST[link]','$_POST[description]','$_POST[type]','$_POST[price]')";
if(!mysql_db_query($dbname,$query)) die(mysql_error());
echo "success in database entry.";

echo "<br />";
echo "<a href=\"------.php\">Click here to return to the form page.</a>";
}

write_xhtml_footer('');

?>

```

---

### Post by bunker on 2007-10-19
I can't tell from your code, but that error usually means auto_increment was not set on the table's key and you did not specify a primary key in an INSERT statement.  Otherwise you might be attempting to INSERT with a key that already exists.  Hard to tell without your database schema.

Hope it helps.

Edit: also remember to sanitise the user input ;).

---


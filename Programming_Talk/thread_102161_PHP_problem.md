---
title: "PHP problem"
date: 2005-12-11
forum: Programming Talk
---

### Post by herrpoon on 2005-12-11
Hi, was looking at php and mysql for the first time today and I'm having a bit of a problem.  From this ebook I've got, I've already entered some data into a mysql database and now I'm trying to get this damn search to work and for it to query the database and display the results as results.php.  

Anyway I'm getting the following error: Parse error: parse error, unexpected '>' in /var/www/books/results.php on line 44.  I've looked and looked and can't seem to find the problem.  Below is the results.php where the problem must be!

```
<html>
<head>
	<title> Book Search Results
</head>
<body>
<h1> Book Search Results</h1>

<?php
// create short variable names
$searchtype=$_POST['searchtype'];
$searchterm=$_POST['searchterm'];
$searchterm= trim($searchterm);

if (!$searchtype || !$searchterm)
{
	echo 'You have not entered any search details.  Please go back and try again.';
	exit;
}

if (!get_magic_quotes_gpc())
{
	$searchtype = addslashes($searchtype);
	$searchterm = addslashes($searchterm);
}

@ $db = mysqli_connect('10.0.0.1', 'name', 'pword', 'database');

if (mysqli_connect_errno())
{
	echo 'Error: Could not connect to database.  Please try agian later.';
	exit;
}

$query = "select * from books where ".$searchtype." like '%".$seachterm."%'";
$result = $db->query($query);

$num_results = $result->num_rows;

echo '<p>Number of books found: '.$num_results.'</p>;

for ($i=0; $i <$num_results; $i++)
{
	$row = $result->fetch_assoc();
	echo '<strong>'.($i+1).'. Title: ';
	echo htmlspecialchars(stripslashes($row['title']));
	echo '</strong><br />Author: ';
	echo stripslashes($row['author']);
	echo '<br />ISBN ' ;
	echo stripslashes($row['isbn']);
	echo '<br />Price: ';
	echo stripslashes($row['price']);
	echo '</p>' ;
}

	$result->free();
	$db->close();

?>
</body>
</html>

```

Any help would be very much appreciated :)

P.s Line 44 is "echo '<strong>'.($i+1).'. Title: ';"

---

### Post by ph0x on 2005-12-11
Add an ' at the end of this line:
[PHP]echo '<p>Number of books found: '.$num_results.'</p>;[/PHP]
I mean: between > and the semicolon ;-)


greetz ph0x

---

### Post by cactus on 2005-12-11
EDIT: Ooops. someone had faster fingers. ;)

---

### Post by M3ta7h3ad on 2005-12-11
You also may want to consider closing the </title> tag at the top as I believe IE will have a heart attack trying to make sense of a non-closed <title> tag.

---

### Post by herrpoon on 2005-12-11
Got it now, many thanks all for your help!

---

### Post by Jonne on 2005-12-11
echo '<p>Number of books found: '.$num_results.'</p>[color=RED]'[/color];

---

### Post by ph0x on 2005-12-11
Not concerning the problem, but here
```
echo 'Error: Could not connect to database.  Please try agian later.';
```
you have switched "a" and "i" in "again".


greetz ph0x

---

### Post by herrpoon on 2005-12-11
[QUOTE=ph0x]Not concerning the problem, but here
```
echo 'Error: Could not connect to database.  Please try agian later.';
```
you have switched "a" and "i" in "again".


greetz ph0x[/QUOTE]

Thanks ;)

---

### Post by herrpoon on 2005-12-11
Hi, another problem - sorry :rolleyes: 

I'm not getting any errors as such but now when I do a search for a book I know that's in my database, it's not coming up with anything.  It's almost as if it's not connecting to the database correctly as it doesn't seem to matter whether or not I even specify a password/username for the database it still shows nothing for results.php.  If it's any help I am doing this on the default ubuntu LAMP install.  Again, thanks for any help.

---

### Post by M3ta7h3ad on 2005-12-11
Get it to print out the variable it just searched for. Make sure its searching for the right thing.

---

### Post by ph0x on 2005-12-11
I don't know how you use to test your scripts but another error could be this one:
with
```
 
$foo=$_POST['foo'];

```
you tell the script to generate the variable $foo out of the value it got from the calling script submitted via method="post".
If you test your script without that calling script before, php generates the variable $foo with no value.
Like M3ta7h3ad said, print out these two variables so you can see if this is the error. If so the script will probably run properly when using it "in whole".
A workaround in order to test the script would be to "hard code" the value of the two variables into your script.


greetz ph0x

---


---
title: "using post and get commands php, html"
date: 2010-03-30
forum: Programming Talk
---

### Post by w0296094 on 2010-03-30
Hey guys,

I want to use the post command to submit information in a form. The i want to receive the results. Later, I want to be able to call back those results with another form. Is it possible to do this with PHP and HTML? 
What I'm looking to accomplish is that php has some limitations regarding making code results look better(html does not have that problem, i believe), and aesthetics is critical to my project. Any input?Should I do just one entire page on the code?Another way to tackle this problem? I'm open to suggestions. 

Below is the code from the first form, and the results page. I want to be able to call back the echo results generated from the results page, that were filtered from the initial form.

  	 	 	 	 	 	  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
 <html>
 <head>
   <meta content="text/html; charset=ISO-8859-1"
  http-equiv="content-type">
   <title>Relational database search</title>
 </head>
 <body>
 <h1> Relational database model search</h1>
 <form method="post"
  action="http://localhost/dbmodel/viewcourseinformation.php"
  name="relationaldb">
 Select your search criteria by:
   <select name="searchtype">
   <option value="Dept_number">dept number</option>
   <option value="Dept_name">Dept name</option>
   <option value="Manager_SSN">SSN</option>
   <option disabled="disabled" selected="selected">choose...</option>
   </select>
   <br>
   <br>
 Type the information<input maxlength="30" name="searchterm"
  value=""><br>
   <br>
 Then, click submit button:<br>
   <button value="Search" name="search"></button><br>
 </form>
 </body>
 </html>
 


code for second page:

$term = $_POST['searchterm'];//$_GET['course'];
$searchtype = $_POST['searchtype']; 
$result = mysql_query("SELECT * FROM `department` WHERE " . $searchtype . "= '" . $term . "'") or die("You have chosen an invalid entry");   
 
echo "<table border='1'>"; 
echo "<tr> <th>Dept number</th> <th>Dept name</th> <th>Manager SSN</th> </tr>"; 
// keeps getting the next row until there are no more to get 
while($row = mysql_fetch_array( $result )) { 
// Print out the contents of each row into a table 
echo "<tr><td>"; 
echo $row['Dept_number']; 
echo "</td><td>"; 
echo $row['Dept_name']; 
echo "</td><td>"; 
echo $row['Manager_SSN']; 
echo "</td></tr>"; 
} 
 
echo "</table>"; 
?>

---

### Post by enz1m3 on 2010-03-30
Well, I'm not sure I get what you want, but doesn't mixing PHP with HTML solve your problem?

You should also be aware you have huge security breaches in your code.

Every variable should be validated for its content before you put it in a MySQL query, and even in there you should add mysql_real_escape_string() with single quotes wrapping the value (unless you're ABSOLUTELY sure it's an integer, that way you don't need those two, but you should cast the integer value).

---

### Post by Hellkeepa on 2010-03-31
HELLo!

First off I've cleaned up the code for you, and added some preliminary security checks. Note that I haven't added input validation, which you need to do yourself, and that I've assumed that the "SSN" is an integer only.
Here's the updated code: [http://pastebin.com/ZyrPzfZP](http://pastebin.com/ZyrPzfZP)
You'll find the "quote_smart ()" function I've used here: [http://norskwebforum.no/viewtopic.php?p=243716](http://norskwebforum.no/viewtopic.php?p=243716)

Then to your problem: What you need to do is to store the resulting array in a database, after serializing it, and then returning the unique ID for that newly created row. You can also add some search words, or even the query itself, along with a "last updated" date, if you want to do caching.
In any case, as soon as you got some unique identifier for that row, then you can use it to select it from the database via another form. So, it's quite simple, even if it may sound complex at first. ;-)

Happy syncin'!

---

### Post by Compyx on 2010-03-31
The 'quote_smart()' function you mention has a little problem: it translates comma's to dots in numbers regardless of locale. That can be easily fixed by examining the locale with localeconv():
[php]
$locale = localeconv();
if ($locale['decimal_point'] == ',') {
    // replace comma with dot
}
[/php]

This still has a small problem: it assumes the end-user inputs their numeric values in their own locale and isn't trying to be smart and input the numbers in the english locale. ;)

---

### Post by Hellkeepa on 2010-03-31
HELLo!

Good catch, I'll notify **Stadskle** about it.

Happy codin'!

---

### Post by enz1m3 on 2010-03-31
wth is going on?! am I the only one who sees the texts all messed up?

EDIT: Ok looks like it's being fixed.

---

### Post by Hellkeepa on 2010-03-31
HELLo!

Nope, you're not. I guess they're just preparing some stuff, or got a slightly early start.

Happy codin'!

---

### Post by w0296094 on 2010-03-31
hellkeepa,

your advice is always useful. All of what you said makes sense. I will be looking at how to store the $row code.
What do you mean by serializing? Is it like turning the command into like a hyperlink or something like that?

---

### Post by Hellkeepa on 2010-03-31
HELLo!

Have a look at PHP's "[serialize ()](http://php.net/serialize)" function, then you'll see what I mean. ;-)

Happy codin'!

---

### Post by w0296094 on 2010-04-01
i managed to pass  the variables with $_SESSION. This is what i did(this page is called storesession):

<?php session_start(); ?> 
<html>
<head>
<title>dbtestpage</title>
</head>
<body>
<?php
//when doing session start, it must be before html script, otherwise whole code may not wok 
session_register ("testsession");   // Create a session variable called testsession 


$_SESSION['testsession']=cranberry;  //sets the value for testsession, in this case cranber.


mysql_connect("localhost", "-----", "-----") or die(mysql_error());
mysql_select_db("projects") or die(mysql_error()); //must store session variable in db 


mysql_query("INSERT INTO test_table VALUES ( '$_SESSION[testsession]')");
//you are inserting session variable 

echo "successfully inserted cranberry"; 
//when this shows on browser, it means you could execute the webpage 

?>
</body>
</html>


This is the page where i output the values(the page is called getsession):

<?php
session_start( );
?>

<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<title>Full Listing</title> 
</head> 
 
<body>

<?php
//need to create new variables, every time you encode or decode session variables,
//you will have use session_start

mysql_connect("localhost", "-----", "-----") or die(mysql_error());
mysql_select_db("projects") or die(mysql_error());

$callsessionvariable = $_SESSION['testsession'];

echo $callsessionvariable;
 
echo "success";

?>

</body> 
</html>


I manage to get the value "cranberry" to the output page. However, after some time if i want to access getsession.php again after some time, the value is not outputted anymore. The only way I can get the value to work again is if I run storesession.php, and then getsession.php. How do I run getsession and pull out the value without having to run storesession more than one time?

In another note(this is what i actually want to do), once I use POST in a form(on say page 1) to go to another page(on say page 2), in that  page2 , i will get the filtered results from POST. Then I would put those results in a $_SESSION on that same page 2, so that I can later acquire them in another page(say page 3, where I would pull out the $_SESSION variable). I'm guessing what will happen is that the filtered post results will be saved to the $_SESSION, but if my value expires, I will have to run page1(with POST) again in order to retain the value from $_SESSION(the value that is displayed on page2, which will also be stored in $_SESSION, and called back on page 3), and I want to avoid running page 1 several times.

---

### Post by Hellkeepa on 2010-04-02
HELLo!

Please use the [****php][/****php] tags when posting PHP code on the forum, makes things a lot easier to read.

Happy codin'!

---

### Post by w0296094 on 2010-04-12
ok i repposted with php tags so that it does not look confusing

i managed to pass  the variables with $_SESSION. This is what i did(this page is called storesession):

[php] session_start();[/php]
<html>
<head>
<title>dbtestpage</title>
</head>
<body>
[php]
//when doing session start, it must be before html script, otherwise whole code may not wok 
session_register ("testsession");   // Create a session variable called testsession 


$_SESSION['testsession']=cranberry;  //sets the value for testsession, in this case cranber.


mysql_connect("localhost", "-----", "-----") or die(mysql_error());
mysql_select_db("projects") or die(mysql_error()); //must store session variable in db 


mysql_query("INSERT INTO test_table VALUES ( '$_SESSION[testsession]')");
//you are inserting session variable 

echo "successfully inserted cranberry"; 
//when this shows on browser, it means you could execute the webpage 

[/php]
</body>
</html>


This is the page where i output the values(the page is called getsession):

[php]
session_start( );
[/php]

<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<title>Full Listing</title> 
</head> 
 
<body>

[php]
//need to create new variables, every time you encode or decode session variables,
//you will have use session_start

mysql_connect("localhost", "-----", "-----") or die(mysql_error());
mysql_select_db("projects") or die(mysql_error());

$callsessionvariable = $_SESSION['testsession'];

echo $callsessionvariable;
 
echo "success";

[/php]

</body> 
</html>


I manage to get the value "cranberry" to the output page. However, after some time if i want to access getsession.php again after some time, the value is not outputted anymore. The only way I can get the value to work again is if I run storesession.php, and then getsession.php. How do I run getsession and pull out the value without having to run storesession more than one time?

In another note(this is what i actually want to do), once I use POST in a form(on say page 1) to go to another page(on say page 2), in that page2 , i will get the filtered results from POST. Then I would put those results in a $_SESSION on that same page 2, so that I can later acquire them in another page(say page 3, where I would pull out the $_SESSION variable). I'm guessing what will happen is that the filtered post results will be saved to the $_SESSION, but if my value expires, I will have to run page1(with POST) again in order to retain the value from $_SESSION(the value that is displayed on page2, which will also be stored in $_SESSION, and called back on page 3), and I want to avoid running page 1 several times.

---

### Post by enz1m3 on 2010-04-12
Ok, first of all, this is not correct:

[php]
$_SESSION['testsession']=cranberry
[/php]

it should be

[php]
$_SESSION['testsession'] = 'cranberry';
[/php]

but maybe it was you when copying that removed those single quotes.

As for your problem of the $_SESSION variable expiring too soon, you can set the limit using the gc_maxlifetime variable of php, for example:

[php]
ini_set('session.gc_maxlifetime', 86400);//-- 86400 seconds = 1 day.
[/php]

You should check these pages for relevant information:

[http://www.php.net/manual/en/ref.session.php](http://www.php.net/manual/en/ref.session.php)
[http://www.unix.com/shell-programming-scripting/16430-session-limit-php.html](http://www.unix.com/shell-programming-scripting/16430-session-limit-php.html)
[http://bytes.com/topic/php/answers/686406-php-session-time-limit](http://bytes.com/topic/php/answers/686406-php-session-time-limit)

---

### Post by w0296094 on 2010-04-13
your suggestion worked like a charm. Now this is probably the last question. I managed to pass variables to another webpage, without having timeout problems. Now I want to store this::

[PHP] 
echo $row['Dept_number']

[/PHP]

into $_SESSION. However everytime I do it, and try to call it, it looks like i get no output.

This is what I did so far


[PHP] 
<?php session_start()?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<title>Full Listing</title> 
</head>
 
<body>
 <?php 
session_register ("testsession1");
// Make a MySQL Connection
mysql_connect("localhost", "----", "----") or die(mysql_error()); 
mysql_select_db("projects") or die(mysql_error()); 
// Get all the data from the "example" table
$term = $_POST['searchterm'];//$_GET['course'];
$searchtype = $_POST['searchtype']; 
$result = mysql_query("SELECT * FROM `department` WHERE " . $searchtype . "= '" . $term . "'") or die("You have chosen an invalid entry");   
echo "<table border='1'>"; 
echo "<tr> <th>Dept number</th> <th>Dept name</th> <th>Manager SSN</th> </tr>"; 
// keeps getting the next row until there are no more to get
while($row = mysql_fetch_array( $result )) { 
// Print out the contents of each row into a table
echo "<tr><td>"; 
echo $row['Dept_number']; 
echo "</td><td>"; 
echo $row['Dept_name']; 
echo "</td><td>"; 
echo $row['Manager_SSN']; 
echo "</td></tr>"; 
} 
echo "</table>";
$sessionvalue = $row['Dept_number'];

$_SESSION['testsession1'] = '$sessionvalue';  
?> 
<br /><a href="http://localhost/index.html">Go back to Database Access Homepage </a><br /> 
</body> 
</html>

[/PHP]

The webpage runs fine and returns no errors. This is the output page:

[PHP]

<?php
session_start( );
?>

<?php

mysql_connect("localhost", "root", "lab99b") or die(mysql_error());
mysql_select_db("projects") or die(mysql_error());

$sessions = $_SESSION['testsession1'];

echo $sessions

?>

[/PHP]

I'm starting to wonder, maybe this is the limitation of $_SESSION(it cant send the outputs).

I also tried 

[PHP]


$_SESSION['testsession1']  =  $row['Dept_number']

[/PHP]

but still it wont work. Suggestions, about using another function that works like $_SESSION, or anything else I could do to $_SESSION to make it work?

BTW I haven't kept my code clean because though it is easier to see in the long run, I have trouble remembering the code symbols in the short run, and I'm a little pressed in time. So to those that have suggested to clena the code, I'm sorry if i havent changed it yet.

---

### Post by enz1m3 on 2010-04-13
Ok, your problem probably is:

[php]
$_SESSION['testsession1'] = '$sessionvalue';
[/php]
that should be
[php]
$_SESSION['testsession1'] = $sessionvalue;
[/php]

It looks like you didn't understand my first correction about the single quotes, so I think you should read this to understand better their usage: [http://php.net/manual/en/language.types.string.php](http://php.net/manual/en/language.types.string.php)

---

### Post by w0296094 on 2010-04-14
sorry about that, i forgot to include that i did try $sessionvalue, and the link returned no results. When I tried '$sessionvalue' it returned the word: $sessionvalue. 
So yes i did try $sessionvalue, but I forgot to include it in my question. Any suggestions why the value would not be stored?

---

### Post by enz1m3 on 2010-04-14
If you try to store a simple thing like 'test', does it work?

---

### Post by w0296094 on 2010-04-14
yeah it works perfectly with words, its just that when i put commands from an output i dont get any value.

---

### Post by enz1m3 on 2010-04-14
oh, so you want to record the output into that session var?

use ob_start(); before the output and $sessionvar = ob_get_clean(); after

---

### Post by w0296094 on 2010-04-14
thanks a lot i finally did it after days of experimentation. if you were right next to me i'd take you out to drink like we do in my region.
anyway, all the best, have a good one.

---

### Post by enz1m3 on 2010-04-14
no problem, simply put [Solved] in the topic title :)

---


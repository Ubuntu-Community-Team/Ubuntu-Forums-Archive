---
title: "Retrieving data from mysql through php"
date: 2011-05-07
forum: Programming Talk
---

### Post by ravikanth.vva on 2011-05-07
i created a data base named books using terrminal and inserted 2 entries

[B][I]mysql> select * from books;
+----+-----------------+-------------+-------------+----------+
| id | name            | author      | publication | quantity |
+----+-----------------+-------------+-------------+----------+
|  1 | web programming | Chris Bates | TMH         |        7 |
|  2 | wireless        | Peter brook | Wrox        |        6 |
+----+-----------------+-------------+-------------+----------+
2 rows in set (0.00 sec)[/I][/B]

and when i try to access from php using following code...nothing gets displayd on my page

[I][B]<html>
<body>
page due
<?php
$con = mysql_connect("localhost","root","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

  [/B][B]
mysql_select_db("books", $con);
$result=mysql_query("select * from books");
while($rows=mysql_fetch_array($result));
{
echo $rows['author'];
echo "<br />";    
    }
mysql_close($con);
?> 
</body>
</html>
[/B] [/I]

need help

---

### Post by ravikanth.vva on 2011-05-07
im using bluefish....this is a home work.. i have the whole idea but im not able get the database working with my php

---

### Post by ravikanth.vva on 2011-05-07
i think the problem is with the line
[I][B]mysql_select_db("books", $con);


[/B][/I]i have the database named books and then created a table books inside it

---

### Post by ravikanth.vva on 2011-05-08
need help ppl

---

### Post by memilanuk on 2011-05-08
For starters... paste the text from you terminal between code or php tags rather than bolding everything.  Makes it easier to read for everyone.

Your code:

[PHP]<html>
<body>
page due
<?php
$con = mysql_connect("localhost","root","password");
if (!$con)
{
die('Could not connect: ' . mysql_error());
}


mysql_select_db("books", $con);

$result=mysql_query("select * from books");

while($rows=mysql_fetch_array($result));
{
echo $rows['author'];
echo "<br />";
}
mysql_close($con);
?>
</body>
</html>[/PHP]

Code from the W3 Schools [example]("http://www.w3schools.com/php/php_mysql_select.asp"):

[php]
<?php
$con = mysql_connect("localhost","peter","abc123");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("my_db", $con);

$result = mysql_query("SELECT * FROM Persons");

while($row = mysql_fetch_array($result))
  {
  echo $row['FirstName'] . " " . $row['LastName'];
  echo "<br />";
  }

mysql_close($con);
?> 
[/php]

Looks right to my eyes; then again I'm no expert.  

Silly question... are the connection credentials right i.e. is the root password really 'passwd'?  I understand if you substituted it when posting for security reasons, but figured maybe worth verifying...

---

### Post by ravikanth.vva on 2011-05-09
yeah the password is right....  i got the output...it k..thanks anyway

---

### Post by ravikanth.vva on 2011-05-09
i think it the case sensitivity in sql commands...i copied the w3scools code and modified it

---

### Post by credomane on 2011-05-09
I see a runtime error.

[php]while($rows=mysql_fetch_array($result));
{
echo $rows['author'];
echo "<br />";
}[/php]
That semi-colon on the first line is considered the end of the loop. The code in the brackets will not execute. This should get it working.
[php]while($rows=mysql_fetch_array($result))
{
echo $rows['author'];
echo "<br />";
}[/php]

I believe this is the more proper way to do the while line.
This is a strict check of the return from mysql_fetch_array. Just in case for some reason the function returns some value that would compare to false with the loose comparison php does by default.
[php]
while(($rows=mysql_fetch_array($result))!==false)
[/php]

---

### Post by dozycat on 2011-05-09
In your navigator, press see code and show us what you got?
And yes is good idea to echo only the author not the following line and see what happens.

---

### Post by ravikanth.vva on 2011-05-09
ive rectified the problem..its working now....thanks anyways

---

### Post by ravikanth.vva on 2011-05-09
hey dozycat...im still working on the work...it got xtended till wednesday
the problem in hand is authenticating the user name and password
check out my code

---

### Post by ravikanth.vva on 2011-05-09
**this is login form**


<html>
<body>
<table frame="box">
<caption><b><i>LOG IN</i></b></caption>
<form action="check.php" method="post">
<tr><td>UserId:</td><td><input type="text" name="login" /></td></tr>
<tr><td>Password:</td><td><input type="text" name="password" /></td></tr>
<tr><td><input type="submit" value="signin"/></td></tr>
</form>
</table>
<p>In this page you can login as an administrator or as staff.The privileges will be different</p>
<p>An administration can make direct changes to database like adding an entry or deleting one,altering the database etc</p>
<p>Staff login can issue from and return books to library</p>
</body>

---

### Post by ravikanth.vva on 2011-05-09
check.php


<html>
<body>
<?php 
if($_POST("login")=="Staff" && $_POST("password")=="staffin")
{ 
    header("Location:staff.php");
    }
    elseif($_POST("login")=="Admin" && $_POST("password")=="strator")
{
    include("admin.php");
    }
    else {echo "check your user name and password";}
</body>
</html>

---

### Post by ravikanth.vva on 2011-05-09
im gettin a blank screen on submit

---

### Post by dozycat on 2011-05-09
It is a good idea to publish the solution.
The why is to permit another person in the same problem try your solution.

---

### Post by ravikanth.vva on 2011-05-09
yeah ive been trying

---

### Post by dozycat on 2011-05-09
go by steps or segmentation.
try first to show the parameters in check.php after submit instead of the logic.
That way you can check if the parameters are all rigth.
After that you can try to change the header without the logic.
The idea is to try everything separated and then try everything together.

---

### Post by ravikanth.vva on 2011-05-09
i know whats happenin...as soon as i hit submit the check.php is being displayed in the frame....the prob is there is no text....i checked condition and am trying to display the staff.php there but i dont know how to open a page in that frame..in html we use target even then there has to be a click right....some onload function can be used maybe.......im very new to web programming

---

### Post by ravikanth.vva on 2011-05-09
is header the appropriate way to do that??

---

### Post by dozycat on 2011-05-09
header("Location:staff.php");
header("http://localhost/staff.php");

that must do it, I do that in one web page we have.

---

### Post by ravikanth.vva on 2011-05-09
k

---

### Post by ravikanth.vva on 2011-05-09
the problem is with if condition itself....ill try and work it out...thanks for ur help dozycat

---

### Post by cgroza on 2011-05-09
> **ravikanth.vva said:**
> the problem is with if condition itself....ill try and work it out...thanks for ur help dozycat
Put an echo statement that prints your variable and see if in respects your condition.
Even easier, put an alert inside your if block, if that gets executed, the alert will show up.

---

### Post by ravikanth.vva on 2011-05-10
i tired it...thats hw i know if clause is the problem

---

### Post by ravikanth.vva on 2011-05-10
i got it.....its a simple syntax error......i think i should stop taking help from ubuntu forums...its too helpful to help and to stop

---


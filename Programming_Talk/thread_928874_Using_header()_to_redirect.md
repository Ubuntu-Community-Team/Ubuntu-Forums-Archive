---
title: "Using header() to redirect"
date: 2008-09-24
forum: Programming Talk
---

### Post by suforum on 2008-09-24
I am writing a script to update a database. Part of the update checks for a duplicate stock number and I want to redirect back to the input form if there is a duplicate. If there is no duplicate, send the user off to another script to finish up the process.

Here is the code I am using:

> //sql check routine
 //check for duplicates in database by stock number
 session_start();
 unset($_SESSION[error]);
 require_once("database.php");
 $stock_num=$_POST[stock_num];
 $_SESSION[stock_num]=$stock_num;
$sql="SELECT * FROM vehicles where stock_num = '$stock_num'";
$result=mysql_query($sql) or die(mysql_error());
if (mysql_num_rows($result)!=0){
    //There is a duplicate stock number so go back to form with an error
    $_SESSION[error]="There is a duplicate";
    }
    if ($_SESSION[error]){
    header("Location: newad.php");
    }

else {
header("Location: preview_text.php");
 }  

No matter what the results of my query, the next script called is always preview_text.php. What am I doing wrong?

____________
[Permanent Links](http://www.submitedge.com)

---

### Post by Reiger on 2008-09-24
Are $stock_nums supposed to be strings (otherwise what are those apostrophes doing _there_)? Does the MySQL dialect allow the use of lowercase 'where'? Wouldn't it help (at least it's better coding practice) to use proper keys (litteral values; unless these are numbers should be proper strings)...?
Also: try print_r($_SESSION); in your follow up script (when it supposedly went 'OK', but in actual fact should;ve gone 'wrong')...

---

### Post by drubin on 2008-09-24
> **Reiger said:**
> Are $stock_nums supposed to be strings (otherwise what are those apostrophes doing _there_)? Does the MySQL dialect allow the use of lowercase 'where'? Wouldn't it help (at least it's better coding practice) to use proper keys (litteral values; unless these are numbers should be proper strings)...?
Also: try print_r($_SESSION); in your follow up script (when it supposedly went 'OK', but in actual fact should;ve gone 'wrong')...

MYsql is in no way case sensitive! But it is a language standard to put reserved words in UPPER case. it makes the code much easier to read. also when you are looking in your logs. It will help.

+1 for the print_r($_SESSION); May I ask why you are trying to store these errors in your $_SESSION array?  Do you NEED access to them the next time the user refreses the page? 

Maybe take a read as to what sessions should be used for. [www.php.net/session](www.php.net/session)

---


---
title: "escaping ' but then it writes a \ to the mysql database"
date: 2011-02-10
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-10
I am using the php mysql escape function
When I run this on a web hosting site, it stores the string with 
the backslash like this in the field o\'henry

this is my string escape
$titles = mysql_real_escape_string($_POST['titles']); 

When I run this locally on my PC, it does not store the \ in the field.

So any ideas?
this is my primitive site where you can see it and add records using an ' to see what happens.
None of the backslashes ever show up on my system like they appear on the web hosted site

[http://www.sdowney717.byethost16.com/mysearch2first.php](http://www.sdowney717.byethost16.com/mysearch2first.php)

---

### Post by sdowney717 on 2011-02-10
I have duplicated the pages here, and I dont get that \ 
On this site it works just as on my home PC.
[http://hcslibrary.freehostingcloud.com/mysearch2first.php](http://hcslibrary.freehostingcloud.com/mysearch2first.php)

---

### Post by sdowney717 on 2011-02-10
[http://stackoverflow.com/questions/173212/mysql-real-escape-string-leaving-slashes-in-mysql](http://stackoverflow.com/questions/173212/mysql-real-escape-string-leaving-slashes-in-mysql)

it seems that host service may have magic quotes on.

[http://blogs.sitepoint.com/2005/03/02/magic-quotes-headaches/](http://blogs.sitepoint.com/2005/03/02/magic-quotes-headaches/)
found a fix here
tested and it works
put this at top of your page

 // Is magic quotes on? 
if (get_magic_quotes_gpc()) { 
// Yes? Strip the added slashes
 $_REQUEST = array_map('stripslashes', $_REQUEST); $_GET = array_map('stripslashes', $_GET); $_POST = array_map('stripslashes', $_POST); $_COOKIE = array_map('stripslashes', $_COOKIE); }

---


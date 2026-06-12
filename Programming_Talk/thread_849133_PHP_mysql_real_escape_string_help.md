---
title: "PHP mysql_real_escape_string help"
date: 2008-07-04
forum: Programming Talk
---

### Post by tmatt95 on 2008-07-04
Over the summer I have set myself the goal of creating a website. To help protect the website from SQL injection, I have tried to get the mysql_real_escape_string() command to work without much success. I am trying to get it to convert a variable before it is used in a select statement. Below is a copy of the code section (the database is brought in on a file before this part of code is included with an include function.)

code:
//Gets the variables from the login form
$username = stripslashes(strip_tags(htmlspecialchars($_POST['username'])));
$password = sha1($_POST['password']);

$test = mysql_real_escape_string($username)

This brings back the error when run:
Warning: mysql_real_escape_string() [function.mysql-real-escape-string]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/buswatch.net/login.php on line 7

Thanks for your help,

Matt

---

### Post by henchman on 2008-07-04
hello!

usually, this error only occurs when you didn't open a mysql connection properly before.

try to do a ```
var_dump( $con );
``` to return the type of your connection variable.

if it's a boolean, then your the script couldn't connect to the mysql server properly as mysql_connect returns false if there is an error connecting to the server... if it's not a boolean, try to hand it on to your mysql_real_escape_string as the second parameter:

```
string mysql_real_escape_string  ( string $unescaped_string  [, resource $link_identifier  ] )
```

---

### Post by henchman on 2008-07-04
oh.. and you should have a look at this code :)

```
stripslashes(strip_tags(htmlspecialchars($_POST['username'])));
```

as htmlspecialchars performs the following actions on your variable:

> #   '<' (less than) becomes '&lt;'
# '>' (greater than) becomes '&gt;' 

and strip_tags afaik seeks for '<' and '>' signs to remove the embraced tags, imho it's useless to strip_tag after htmlspecialchars, because you will have no tags...

also have a look at the examples on [http://www.php.net/stripslashes](http://www.php.net/stripslashes), to look whether magic_quotes_qpc is enabled or not

---

### Post by tmatt95 on 2008-07-04
Thanks for your quick response henchman. Below is the resultant output from the command **var_dump( $db );**:
*object(mysqli)#1 (0) { }*

Here is the line of code that I use to connect to the database as well if that helps:

[I]/*Database connection info*/
@ $db = new mysqli('localhost','variable','passwordwouldbehere','variable');[/I]

(Have taken out the identifiable information before posting the above code)

I have also tried adding the name of the database. With the code for the escape string looking like this:

*$test = mysql_real_escape_string  ($username,$db);*

I now get this error:
*Warning: mysql_real_escape_string() expects parameter 2 to be resource, object given in /var/www/buswatch.net/login.php on line 7 *


Matt

P.S Thanks for your advice on the strip slashes/ tags. Will remove the tags that are not needed.

---

### Post by tmatt95 on 2008-07-04
Thanks for your help. Found that the database connection was wrong and adjusted it to:

@ $db = mysql_connect('localhost','data','password','data');


and adjusted the calls below etc and it now outputs with out causing an error. Is that a good way to do it? 

Regards,

Matt

---

### Post by drubin on 2008-07-04
> and adjusted the calls below etc and it now outputs with out causing an error. Is that a good way to do it?

It is ok... to hide such detail from end users but I would DEF log if it fails ie.

[PHP]$db=@mysql_connect('localhost','data','password','data' );
if(!$db){
  error_log('Could not connect to db,{add date/time/ip details}',3,'/var/logs/weblog.log');
include('error_page.php'); //Show a nicely formated PR acceptable error.... 
exit();//stop processing rest of page
}[/PHP]

---

### Post by henchman on 2008-07-04
Ahh :)

you mixed mysql and  mysqli. one should also either stick to object notation or "function notation" (dont know if it's called like this)

just have a look at the official examples on php.net

[http://www.php.net/manual/en/mysqli.real-escape-string.php](http://www.php.net/manual/en/mysqli.real-escape-string.php)

for a connection/query example of mysqli in both object and "function" notation and the same for mysql

[http://www.php.net/manual/en/function.mysql-real-escape-string.php](http://www.php.net/manual/en/function.mysql-real-escape-string.php)

the normal mysql functions are the "old" way to connect and thus, they do not support object notations, because "real" class support was only added with PHP5

You should definitely have a look at the "new" cool & shiny PDOs:
[http://de.php.net/pdo](http://de.php.net/pdo)

---


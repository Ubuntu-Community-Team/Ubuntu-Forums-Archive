---
title: "setting a cookie with php.."
date: 2008-08-08
forum: Programming Talk
---

### Post by Mia_tech on 2008-08-08
I'm using a login form that authenticates the user against a mysql database and at the same time it sets the cookie the only problem is that is not setting the cookie, I'm using the cookie editor firefox addon and is not showing any cookie been set after login, this is what I'm using 
[PHP]setcookie("site_user", $u_name, date() + 31536000, "/");[/PHP]
the $u_name is a variable set from the username column from the database table, followed by the expiration date which is set to expire a year from now...
why is the cookie not been set?

any help appreciated

thanks

---

### Post by Bachstelze on 2008-08-08
Did you put that at the very beginning of your script?

---

### Post by cszikszoy on 2008-08-08
The PHP manual is simply amazing.  It has tons of information and tips: [http://de3.php.net/setcookie](http://de3.php.net/setcookie)

> **setcookie()** defines a cookie to be sent along with the    rest of the HTTP headers. Like other headers, cookies must be sent    *before* any output from your script (this is a    protocol restriction). This requires that you place calls to this function    prior to any output, including *<html>* and    *<head>* tags as well as any whitespace.   

---

### Post by Mia_tech on 2008-08-08
> **HymnToLife said:**
> Did you put that at the very beginning of your script?

no, but I did set the cookie before sending the html header, here's the script, maybe that way you could assist me better....
[PHP]<?php
//###########################
//##   name: login.php     ##
//## by: Jorge L. Vazquez  ##
//##      8/7/08           ##
//###########################
//declaring variables
$uname = $_POST['username'];
$pass = $_POST['password'];
//check for required fields
if ((!$uname) || (!$pass)) {
	echo "<h3>Missing username or password!</h3>";
	echo "<a href=/login.htm>back to login</a>";
	exit;
}

//open mysql connection
$conn = mysql_connect("10.200.50.11", "root", "password") or die(mysql_error());
mysql_select_db("test", $conn) or die(mysql_error());

//create and issue the query
$sql = "SELECT * FROM members WHERE username = '$uname' AND password = '$pass'";
$result = mysql_query($sql, $conn) or die(mysql_error());

//getting the number of rows
if (mysql_num_rows($result) == 1) {
	//if authorized get the values of username 
	$u_name = mysql_result($result, 0, 'username');
		
	//setting the cookie
	setcookie("site_user", $u_name, date() + 31536000, "/");
	
	//greeting the user
	$msg = "<P><h3>Welcome $u_name!</h3></p>";
	$msg .= "<br><a href=/login.htm>logout</a>";
	}
else {
	//redirect back to login form if not authorized
	echo "<h3>Wrong username or password!</h3>";
	echo "<br><a href=/login.htm>back to login</a>";
	exit;
	}
?>
<html>
<body bgcolor="#000000">
<font color="#00ff00">
<?php print "$msg"; ?>
</font>
</body>
</html>
[/PHP]

thanks

---

### Post by Mia_tech on 2008-08-08
ok guys there was something wrong with the way I was setting up the cookie, and it was that I was using the date() function instead of the time() function to set the expiration date... as soon as corrected it worked
[PHP]setcookie("site_user", $u_name, time() + 31536000, "/");[/PHP]

thanks

---

### Post by cszikszoy on 2008-08-08
I'm sure this can cause you problems:

```

[COLOR=#000000][COLOR=#FF8000]//check for required fields 
[/COLOR][COLOR=#007700]if ((![/COLOR][COLOR=#0000BB]$uname[/COLOR][COLOR=#007700]) || (![/COLOR][COLOR=#0000BB]$pass[/COLOR][COLOR=#007700])) { 
    echo [/COLOR][COLOR=#DD0000]"<h3>Missing username or password!</h3>"[/COLOR][COLOR=#007700]; 
    echo [/COLOR][COLOR=#DD0000]"<a href=/login.htm>back to login</a>"[/COLOR][COLOR=#007700]; 
    exit; 
} [/COLOR][/COLOR]

```

When ot says to put it before sending the HTML headers what this means is you can't send ANY data to the webbrowser... HTML headers or echos.

---

### Post by mike_g on 2008-08-08
Yeah, I'd do it with a redirect:
```

if ((!$uname) || (!$pass)) { 
   header("Location: login.php");	
} 
```
Also, you may want to look at storing the user info to the session instead of a cookie; its easy to do.

---

### Post by Mia_tech on 2008-08-08
> **mike_g said:**
> Yeah, I'd do it with a redirect:
```

if ((!$uname) || (!$pass)) { 
   header("Location: login.php");	
} 
```
Also, you may want to look at storing the user info to the session instead of a cookie; its easy to do.

why?... what is the difference between cookies and sessions id? I thought they were kind of the same thing

thanks

---


---
title: "giving access to pages based on cookie..."
date: 2008-08-08
forum: Programming Talk
---

### Post by Mia_tech on 2008-08-08
I'm doing most of the website programming in php....and I want to be able to give access/redirect to specific pages after a user login based on the cookie set during the login process, and once the user is at that page check his credential... could anyone advise me on what's the best way to go about this?


thanks

---

### Post by slavik on 2008-08-08
you need to store the user's permissions based on his credentials

---

### Post by Mia_tech on 2008-08-09
I wish to accomplish this using session id or cookies


thanks

---

### Post by Linux&amp;Gsus on 2008-08-09
I'm not sure if I fully understood what you want to do. However, I hope you don't rely on these cookies beyond one session. There are people like me who have set Firefox to delete all cookies when closing.
Wouldn't it be better to have all those setting database driven with different user groups getting access to different content? But then I really don't know what you have in mind to do.

Maybe these sites are of some help:
[http://www.w3schools.com/js/js_cookies.asp](http://www.w3schools.com/js/js_cookies.asp) - from a JavaScript perspective
[http://www.webcheatsheet.com/php/cookies.php](http://www.webcheatsheet.com/php/cookies.php) - from a PHP perspective

What kind of information you set in the cookies is up to you. User credentials / group membership / status / what ever. Read it out and serve a page accordingly with the appropriate navigation if necessary.
Well, I don't know if it would work like that. It's just a spontaneous idea without thinking in depth about it.

Cheers.

---

### Post by Mia_tech on 2008-08-09
this is for a project in which I hope to demonstrate cookie or session impersonation, when a malicious user will change his cookie or session settings and inject it back into the browser therefore impersonating a different user...

I have been able to set a cookie but when I change the setting with firefox cookie editor and inject it back to the web page it wont reflect the new user, instead is sending all info against the database and giving me back the same cookie, maybe I'll have to change my login script..here's the php code I'm using
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
	setcookie("site_user", $u_name, time() + 31536000, "/");
	
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

I know this not entirely programming but also security, but any ideas are welcome

thanks

---

### Post by Mia_tech on 2008-08-09
actually it was easier that I thought, and once there's a page that is retrieving the cookie and giving you access based on that, you can actually change the cookie and reinject it back to the browser, I test it with this little script
[PHP]<?php
//retrieving cookie and setting variable
$cookie = $_COOKIE['site_user'];

//telling you who are you..
if ( $cookie == "admin") {
	echo "welcome administrator";
	}
else {
	echo "You are regular user";
	}
?>[/PHP]

I know that hard coding usernames on your pages is a dead give away, but this is just a proof of concept

thanks all for the links Linux&Gsus

---

### Post by Linux&amp;Gsus on 2008-08-09
No worries. And congratulations. :)
Now you can enjoy a self bought cookie. :KS

Cheers.

---


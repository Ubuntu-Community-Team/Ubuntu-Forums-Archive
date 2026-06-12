---
title: "Creating a cookie if admin, different one if normal user."
date: 2009-12-01
forum: Programming Talk
---

### Post by gillespiea on 2009-12-01
Hi folks.
I'm trying to keep things simple with my site and i'd quite like to have a cookie made depending on wither the user is an admin or not (admin == 1).

The following is the code i have at the moment and this only creates a cookie and does not select admin (because i don't know what to do to create a query to use the admin == 1 or 0)

[php]//create and issue the query

$sql = "SELECT f_name, l_name FROM users WHERE username = '".$_POST["username"]."' AND password = PASSWORD('".$_POST["password"]."')";

$result = mysqli_query($mysqli, $sql) or die(mysqli_error($mysqli));



//get the number of rows in the result set; should be 1 if a match

if (mysqli_num_rows($result) == 1) {



	//if authorized, get the values of f_name l_name

	while ($info = mysqli_fetch_array($result)) {

		$f_name = stripslashes($info['f_name']);

		$l_name = stripslashes($info['l_name']);


	}



	//set authorization cookie

	setcookie("auth", "1", 0, "/", "127.0.0.1", 0);



	//create display string

	$display_block = "

	<p>".$f_name." ".$l_name." is authorized!</p>

	<h2>Authorized Users' Menu:</h2>

	<ul>

	<li><a href=\"/admin/addnews.php\">Add News</a></li>

	</ul>";

} else {

	//redirect back to login form if not authorized

	header("Location: index.php");

	exit;

}[/php]

anyone able to help create my query as i'm very new to php and mysql?
I'm very lost.

---

### Post by gillespiea on 2009-12-01
Think i got it with this code.
If anyone else can see anything wrong with it please let me know.
cheers.

[php]<?php

//check for required fields from the form

if ((!isset($_POST["username"])) || (!isset($_POST["password"]))) {

	header("Location: index.html");

	exit;

}



//connect to server and select database

$mysqli = mysqli_connect("localhost", "yarpdata", "loptis@", "yarpdata");



//create and issue the query

$sql = "SELECT f_name, l_name, admin FROM users WHERE username = '".$_POST["username"]."' AND password = PASSWORD('".$_POST["password"]."')";

$result = mysqli_query($mysqli, $sql) or die(mysqli_error($mysqli));



//get the number of rows in the result set; should be 1 if a match

if (mysqli_num_rows($result) == 1) {



	//if authorized, get the values of f_name l_name

	while ($info = mysqli_fetch_array($result)) {


		$f_name = stripslashes($info['f_name']);

		$l_name = stripslashes($info['l_name']);
		$admin = stripslashes($info['admin']);


	}

	//create display string

	$display_block = "

	<p>".$f_name." ".$l_name." is authorized!</p>

	<h2>Authorized Users' Menu:</h2>

	<ul>

	<li><a href=\"/admin/\">Add News</a></li>

	</ul>";

} else {

	//redirect back to login form if not authorized

	header("Location: index.php");

	exit;

}

if ($admin == '1')
	{
	setcookie("adminauth", "1", 0, "/", "127.0.0.1", 0);
	}

	

else	{
	setcookie("auth", "1", 0, "/", "127.0.0.1", 0);

	}




?>[/php]

---

### Post by bsharp on 2009-12-01
You need to cleanse the entered form data before querying the DB when you do the login check to protect from SQL injection attacks. E.G:

```
[b]//cleanse here

$uname = mysqli_real_escape_string($_POST['username'], $mysqli);
$passwd = mysqli_real_escape_string($_POST['password'], $mysqli);[/b]

//create and issue the query

$sql = "SELECT f_name, l_name, admin FROM users WHERE username = '".**$uname**."' AND password = PASSWORD('".**$passwd**."')";

$result = mysqli_query($mysqli, $sql) or die(mysqli_error($mysqli));


?> 
```

---

### Post by nelfin on 2009-12-01
I feel obliged to make a comment about SQL injection here. You should use mysqli_prepare and mysqli_stmt_bind_params to prevent people from injecting arbitrary SQL code in the post fields, a la

```
Username: ' OR admin='1' LIMIT 1; --
Password: fakepassword
```

Which would in turn be concatenated into your query string, resulting in it looking like this:

```
SELECT f_name, l_name, admin FROM users WHERE username = '' OR admin = '1' LIMIT 1; -- AND password = PASSWORD('fakepassword');
```

Which would have the end result being that the user gets logged in as the first admin.

You can fix this by going:

[PHP]$sql = 'SELECT f_name, l_name, admin FROM users WHERE username = ? AND password = PASSWORD(?);';

$stmt = mysqli_stmt_prepare($mysqli, $sql);
mysqli_stmt_bind_params($stmt, 'ss', $_POST['username'], $_POST['password']);[/PHP]

Read up in the PHP docs for the rest of the stuff about binding results:
 [http://php.net/manual/en/mysqli-stmt.bind-result.php](http://php.net/manual/en/mysqli-stmt.bind-result.php)
 [http://php.net/manual/en/mysqli-stmt.fetch.php](http://php.net/manual/en/mysqli-stmt.fetch.php)

Also, if you are going to be using this cookie to determine whether someone is an admin later on/in different parts of the site, it would be better to use $_SESSION, otherwise an end-user could just edit their cookie and set adminauth=1, thus fooling the rest of the site.

EDIT: looks like bsharp beat me to it.

---

### Post by gillespiea on 2009-12-02
Thanks very much, very usefull info :)

I've had a good look over what i need the site to do and i agree, using sessions is the best way to go.

Again thanks for your help.

---


---
title: "Session problem"
date: 2005-12-20
forum: Programming Talk
---

### Post by gruszczy on 2005-12-20
I have some problems with sessions in php. This is the message I receive:

```
Warning: session_start(): Cannot send session cookie - headers already sent by (output started at /var/www/usos/logowanie.php:4) in /var/www/usos/logowanie.php on line 13

Warning: session_start(): Cannot send session cache limiter - headers already sent (output started at /var/www/usos/logowanie.php:4) in /var/www/usos/logowanie.php on line 13
```

The php code looks likes this:

```

	<?php
		$database = pg_connect("host=localhost dbname=bdlab user= password=");
		$login = $_POST['login'];
		$password = $_POST['password'];
		$query = "SELECT zaloguj('$login','$password');";
		$query = pg_query($database, $query);
		$result = pg_fetch_row($query);
		pg_close($database);
		if ($result[0] != -1){
			session_start();
		}
		if ($result[0] == 1)
			$typ = "student";
		//	echo '<meta http-equiv="refresh" content="20 URL=index.php">';
		if ($result[0] == 10)
			$typ = "administrator";
		//	echo '<meta http-equiv="refresh" content="0 URL=panel_administratora.php">';
		
	?>
```

Can anyone help me and tell, what's the problem? I would really appreciate some help.. I cannot start session, and can't register any session variables.

---

### Post by tbrownaw on 2005-12-21
Is there anything before the <?php tag? (Including whitespace, etc.) The '<' character in the '<?php' should be the first character in the file.

---

### Post by sapo on 2005-12-21
You have the wrong idea about sessions dude..

You should aways start the session at the beginning of the file.. to avoid problems.. try something like it:

[php]<?php
session_start();
if($_POST) {
	$database = pg_connect("host=localhost dbname=bdlab user= password=");
	$login = addslashes($_POST['login']);
	$password = addslashes($_POST['password']);
	$query = "SELECT zaloguj('$login','$password');";
	$query = pg_query($database, $query);
	$result = pg_fetch_row($query);
	pg_close($database);
	if ($result[0] != -1){
		$_SESSION['whatever'] = true;
	}
	if ($result[0] == 1) {
		$_SESSION['typ'] = "student";
		header("Location: another.php");
	}

	if ($result[0] == 10) {
		$_SESSION['typ'] = "administrator";
		header("Location: forthehooooooooorde.php");
	}
} else {
	die("Error!");
}
?>[/php]

And in the other page use something like this:

[php]<?
session_start();
if($_SESSION['typ'] == "admininistrator") {
	echo "You are the admin dude!";
} elseif($_SESSION['typ'] == "student")  {
	echo "You are a student!"
} else {
	echo "You are NOTHING!";
}
?>[/php]

And dont use meta-refresh, its ugly =x

---

### Post by gruszczy on 2005-12-23
I went home for christmas, but as soon as I get to my other home I'll try it. Thanks for your help.

---

### Post by gruszczy on 2006-01-03
Well, it seems that you are perfectly right - I just didn't understand how the session works. Thanks a lot, I'm step closer to the end ;)

---

### Post by NetCutter on 2006-08-22
Hi,
I have one problem with the php session!
They just does not works!
Look: These 2 scripts does not works!!!
[PHP]<?php
session_start();
// Use $HTTP_SESSION_VARS with PHP 4.0.6 or less
if (!isset($_SESSION['count'])) {
   $_SESSION['count'] = 0;
} else {
   $_SESSION['count']++;
}
?> [/PHP]
[PHP]<?php
session_start();
// Use $HTTP_SESSION_VARS with PHP 4.0.6 or less
unset($_SESSION['count']);
?> [/PHP]

---

### Post by indytim on 2006-08-23
And the error message is..... (besides just doesn't work)??

IndyTim

---

### Post by NetCutter on 2006-08-23
No error message!Just the session doesn't work!
Look this code:
Script1.php:
[PHP]<?php
session_start();
$_SESSION['color']="blue";
?>
<a href="script2.php">Go to Script2.php</a>[/PHP]
script2.php:
[PHP]<?php
session_start();
if(isset($_SESSION['color']))
             echo "Value of color is: ".$_SESSION['color'];
else echo "Color is NOT set";
?>[/PHP]
And the browser give me:
Color is NOT set:(

---

### Post by indytim on 2006-08-23
I'm not sure what variables are depreciated in php5 (if you're using).  Try something like the following to get you started

[PHP]session_start();
$color="blue";
session_register("color");

[/PHP]
call your next program
[PHP]<?PHP
session_start;
print '<br> color='.$color;
?>[/PHP]

---

### Post by indytim on 2006-08-23
second program should be: 
[PHP]<?PHP
session_start();

blah and blah[/PHP]

Sorry for the creeping digititus!

---

### Post by NetCutter on 2006-08-23
[HTML]Warning: Unknown: Your script possibly relies on a session side-effect which existed until PHP 4.2.3. Please be advised that the session extension does not consider global variables as a source of data, unless register_globals is enabled. You can disable this functionality and this warning by setting session.bug_compat_42 or session.bug_compat_warn to off, respectively. in Unknown on line 0[/HTML]

---

### Post by NetCutter on 2006-08-26
So?Can somebody help me?

---

### Post by ifokkema on 2006-08-26
> **NetCutter said:**
> Hi,
I have one problem with the php session!
They just does not works!
Look: These 2 scripts does not works!!!
[PHP]<?php
session_start();
// Use $HTTP_SESSION_VARS with PHP 4.0.6 or less
if (!isset($_SESSION['count'])) {
   $_SESSION['count'] = 0;
} else {
   $_SESSION['count']++;
}
?> [/PHP]
[PHP]<?php
session_start();
// Use $HTTP_SESSION_VARS with PHP 4.0.6 or less
unset($_SESSION['count']);
?> [/PHP]

These scripts run fine on my install. Seems like your configuration is not working properly. Try running a single script, putting something in $_SESSION and incrementing that. Refresh that page and use a var_dump on $_SESSION to see what you've got.

---

### Post by hagen00 on 2006-08-27
> **NetCutter said:**
> [HTML]Warning: Unknown: Your script possibly relies on a session side-effect which existed until PHP 4.2.3. Please be advised that the session extension does not consider global variables as a source of data, unless register_globals is enabled. You can disable this functionality and this warning by setting session.bug_compat_42 or session.bug_compat_warn to off, respectively. in Unknown on line 0[/HTML]

Don't worry about that. That's just a warning. It says your script possibly relies on a session side-effect. But it doesn't. Turn the warning off by editing php.ini by (like the message says) setting session.bug_compat_42 or session.bug_compat_warn to off, respectively. Then restart apache.

---

### Post by ifokkema on 2006-08-27
The original script didn't create the warning, because it wasn't using session_register(). I always just use the $_SESSION array. No idea though what the pros and cons are of using $_SESSION above session_register() and such.

---


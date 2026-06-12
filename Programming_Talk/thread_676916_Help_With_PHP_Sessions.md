---
title: "Help With PHP Sessions"
date: 2008-01-24
forum: Programming Talk
---

### Post by dhtseany on 2008-01-24
Hey all, first and foremost I know sessions are not secure :)

I'm having a problem with trying to echo the username of the logged in user. Here is my code I use for "login.php":
```

<?php
session_start();

$errorMessage = '';
if (isset($_POST['txtUserId']) && isset($_POST['txtPassword'])) {

require('ext_auth.php');

   $user = $_POST['txtUserId'];
   $pass = $_POST["txtPassword"];
   $sql = "SELECT username FROM secure WHERE `username` = '$user' AND `password` = '$pass'";

   $result = mysql_query($sql)
             or die('Query failed. ' . mysql_error());

   if (mysql_num_rows($result) == 1) {
	  $_SESSION['user'] = true;
	  	  **$_SESSION['user'] = $_POST['txtUserId'];**

      header('Location: main.php');
      exit;
   } else {
      $errorMessage = 'Sorry, wrong user id / password';
   }

  
}
?>
<?php
include('../include/1.php');
?>
<?php
if ($errorMessage != '') {
?>
<p align="center"><strong><font color="#990000"><?php echo $errorMessage; ?></font></strong></p>
<?php
}
?>
<form method="post" name="frmLogin" id="frmLogin">
<center>
Please Login:<br>
Username:<input name="txtUserId" type="text" id="txtUserId"><br>
Password:<input name="txtPassword" type="password" id="txtPassword"><br>
<input type="submit" name="btnLogin" value="Login"></td>
</center>
</form>
<?php
include('../include/2.php');
?>

```

The problem occurring is my session is not being set correctly. Notice the bold line... If I remove it everything works fine but then I can't echo the user's username. 

Something odd to note is if I remove that line after attempting a session, it works the way it's supposed to up until I log out and then restore the session; the username disappears. Any ideas on what I'm doing wrong? If I didn't explain it well enough let me know and I'll try again.

Thanks for the help in advance :)

Peace

Sean

---

### Post by deuce868 on 2008-01-24
Did you notice these two lines together, one right after the other:

```

$_SESSION['user'] = true;
$_SESSION['user'] = $_POST['txtUserId'];

```

So which did you want? true, or the text string. It's not holding both.

---

### Post by dhtseany on 2008-01-24
What I need is the session's name to be set to the username used to log in and create the session. That was my attempt at trying to make that happen.

---

### Post by deuce868 on 2008-01-24
I'd strongly encourage you to try to look up some of the many tutorials on implementing a login system in PHP. 

1) Please use mysql_real_escape_string, or PDO with prepared queries, or anything to prevent the sql injection attacks that code is open to
2) Please tell me you're not storing plain text password strings in the database
3) Once you do session_start() you have a session. Anything you put in $_SESSION will be available on any other pages that also run session_start() on them. 

Here's a tutorial a quick search came up with:
[http://www.devshed.com/c/a/PHP/Creating-a-Secure-PHP-Login-Script/](http://www.devshed.com/c/a/PHP/Creating-a-Secure-PHP-Login-Script/)

There are also already a number of auth systems out there for PHP you can use and trust more.

---

### Post by dhtseany on 2008-01-24
Yes, my code is currently 100% unsecured. I'm aware of that as I'm building my site from the ground up and then securing the hell out of it.

However, I wasn't aware there as session alternatives. Any suggestions?

Thanks,

Sean

---

### Post by deuce868 on 2008-01-24
I just use the framework we've got at work, but pear has one for example. 

[http://pear.php.net/package/LiveUser](http://pear.php.net/package/LiveUser)

As another tip, don't think of security as something you lay on top after the fact. That method ends up with too many holes you forgot about along the way. Always develop so that if it's running tomorrow and you don't have time to touch it for a week, you can still sleep at night. 

I've never seen a project that got all the way developed and then had time to go back through every inch of it.

---


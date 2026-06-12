---
title: "As usual... PHP Hates me"
date: 2008-02-07
forum: Programming Talk
---

### Post by dhtseany on 2008-02-07
So hi... PHP doesn't appear to be submitting inputted information into mysql. Could someone have a look at see if anything is obvious?

Thanks,

Sean
```

<?php

session_start();

if (!isset($_SESSION['session']) 

	|| $_SESSION['session'] !== true) {

   echo"<meta http-equiv='refresh' content='0;URL=login.php' />";

   echo"Please log in...";

   exit;

}



if (!isset($_SESSION['session'])

   || $_SESSION['session'] !== false) {

require('ext_auth.php');

 if(isset($_POST['Submit']) && !$errors) 

 {

echo "<h1>Submission Successful!</h1>";

$date = $_POST['date'];

$s_title = $_POST['s_title'];

$t_price = $_POST['t_price'];

$v_name = $_POST['v_name'];


$query = "INSERT INTO shows (date, s_title, t_price, v_name) VALUES ('$date', '$s_title', '$t_price', '$v_name')";

$result = mysql_query($query) or die(mysql_error());

 }

echo "
<html>
<head>
<title>TSR Management Utility:: Add a show</title>
</head>

<body>
<b>Adding a show:</b><br>
<form name='s_add' method='post' enctype='multipart/form-data'  action='add_show.php'>
Show Date:<input size='20' name='date'><br>
Show Title: <input size='20' name='s_title'><br>
Ticket Price:<input size='20' name='t_price'><br>
Venue: <input size='20' name='v_name'><br>
<input type='submit' value='Add Show'><input type='submit' value='Cancel'>
</form>
</body>
</html>
";}
?>



```

---

### Post by mike_g on 2008-02-07
In the code you posted you havent linked to the database. Heres an example I just grabbed from somewhere:
```
<?php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = 'password';

$conn = mysql_connect($dbhost, $dbuser, $dbpass) or die  ('Error connecting to mysql');

$dbname = 'petstore';
mysql_select_db($dbname);

// Do stuff

mysql_close($conn);
?>
```
Dont know if thats any help.

Edit: I think you will also need to select a table from it too.

---

### Post by DrMega on 2008-02-07
Your PHP is running before you start with any HTML so your browser won't give you any clues. After you run it, right click on the page and view source. I bet at the top there will be fatal errors because you haven't opened your DB connection.

---

### Post by dhtseany on 2008-02-07
```

require('ext_auth.php');

```

...opens my db connection.

What do you mean my html is appearing after my php?

If I'm not mistaken using the...
```

 if(isset($_POST['Submit']) && !$errors) 

 {

echo "<h1>Submission Successful!</h1>";

$date = $_POST['date'];

$s_title = $_POST[
.......

```

...is where the info is actually submitting the info to the database.

BTW, thanks for responding :)

Sean

---

### Post by winch on 2008-02-07
```

if (!isset($_SESSION['session'])

   || $_SESSION['session'] !== false)
require('ext_auth.php');

```

I believe the problem is here. You only try to insert to the db if $_SESSION['session'] is not set or $_SESSION['session'] is not equal to false. That doesn't sound right. Presumably you need to be logged to insert to the db so $_SESSION['session'] would be set to something.

---

### Post by DrMega on 2008-02-07
> **dhtseany said:**
> What do you mean my html is appearing after my php?

Sorry. You are right. I must drink more coffee. I quickly scanned down your code and failed to notice that you were output the HTML content directly from your PHP script. I thought your PHP was running before you sent the HTML like in the form:

```

<?php

do_some_php_stuff();
?>

<HTML>
...

```

I was wrong. As others have suggested, I'd look more closely around the conditional expression where you test your session variable. Maybe put an echo message just before the test, just before the DB insert if the condition is true, and in the else if the condition is false, so you can see at a glance which chunks of code are running and which aren't.

One tip, if you think there's any risk of echo output being left in by mistake, output your debug messages wrapped in HTML comments so they won't appear in the browser and you have to view source to see them. I.e.

```

echo "<!-- Some debug message-->";

```

---

### Post by Bronto on 2008-02-07
Are you sure you're sending the right data types to MySQL?

---

### Post by tosk on 2008-02-08
Have you initialized the $errors variable? I don't see it anywhere.

Also, post the last few lines from /var/log/php5/error.log

---

### Post by dhtseany on 2008-02-08
Hey all, thanks for the help!

First, my "/var/log/php5/error.log" is empty; no errors evidentally.

Let me give a little more insight to what this page is about... I am a part owner of a music promotions company (like we put on shows) and this is the start of a show mgt. system. It's all being run locally so security isn't a priority at all :). I'm running UB 7.10 and I believe I've installed LAMP correctly as I didn't see anything resembling errors during or after the install. 

Now, the strange thing is that this code pretty much worked flawlessly when I had it on this cheap hosting for my other company's website. I figured that I put so much work/research into that code that I might as well rip it off :)

Anyways, so now ya'll know what's up.

Tosk, what does "$errors" mean?

Thanks for all the help.

Peace
Sean

---

### Post by deuce868 on 2008-02-08
I'm going to bet that this is trying to use registed globals. You don't actually get the data anywhere. 

```

$query = "INSERT INTO shows (date, s_title, t_price, v_name) VALUES ('$date', '$s_title', '$t_price', '$v_name')";

```

Unless there's a line somewhere does does something like:
```

$date = $_POST['date'];
$s_title = $_POST['title']
...

```

This there's no data there. 

Now there is a ton wrong with the code (ok..things that I'd not do) and you don't seem to know much since you're asking what "$errors mean" when it's sitting in the code you posted. 
```

 if(isset($_POST['Submit']) && !$errors) 

```

If you want to debug this, start using var_dump or print_r on the variables you have there and figure out what's not right. Perhaps $errors is true for some reason, maybe this code assumes registered global (please please no...), and maybe it's something else.

---

### Post by dhtseany on 2008-02-08
> **deuce868 said:**
> 
Unless there's a line somewhere does does something like:
```

$date = $_POST['date'];
$s_title = $_POST['title']
...

```

Actually, there is.

> **deuce868 said:**
> 
and you don't seem to know much since you're asking what "$errors mean" when it's sitting in the code you posted. 
```

 if(isset($_POST['Submit']) && !$errors) 

```


Now that you've pointed out what you meant, yes I do know what you're talking about.

---

### Post by tosk on 2008-02-08
```
isset($_POST['Submit'])
```

See this line? Submit is an unknown variable. Look at your form below. Your submit button is there alright, but it's missing the **name** attribute.

Change this:
```
<input type='submit' value='Add Show'><input type='submit' value='Cancel'>
```
to:
```
<input type='submit' name='submit' value='Add Show'><input type='submit' name='submit' value='Cancel'>
```

And change this:
```
 if(isset($_POST['Submit']) && !$errors) 
```
to:
```
 if($_POST['submit'] == "Add Show" && !$errors) 
```

That should take care of the problem.

You should also put this:
```
$errors = false;
```
underneath this line:
```
$v_name = $_POST['v_name'];
```
...at least until you go back and actually add error checking to the form.

---

### Post by dhtseany on 2008-02-08
Tosk, you are a badass :)

Thanks for your help; that did it! I always thought the "isset($_POST['Submit'])" (submit part) was just a generic/universal part. Thanks for the learnin' :)

Peace

Sean

---


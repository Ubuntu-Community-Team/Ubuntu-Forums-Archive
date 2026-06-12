---
title: "PHP user sign up page check if username / email exists before creating user"
date: 2009-12-16
forum: Programming Talk
---

### Post by gillespiea on 2009-12-16
Hi folks.

If you are on this part of the forums alot you will probably have noticed that i am a beginner to PHP and MYSQL.

I've been searching the Internet for quite some time to try find out how i can check my users database to see if the username or email already exists in the database. But cant find anything that meets my needs.

The details that will be placed into the database come from a page called signup.php and lead to the following code (this isn't all of it, just the php required for this post)

[php]
<?php session_start(); ?>
<?php

include("../includes/config.php");

doDB();



//check for required fields from the form

if ((!$_POST["username"]) || (!$_POST["password"]) || (!$_POST["screenname"]) || (!$_POST["f_name"]) || (!$_POST["l_name"]) || (!$_POST["email"])) {

	header("Location: signup.php");

	exit;

}

//check if username exists



//create user

$add_topic_sql = "INSERT INTO users (username, password, screenname, f_name, l_name, email, admin) VALUES ('".$_POST["username"]."', PASSWORD('".$_POST["password"]."'), '".$_POST["screenname"]."', '".$_POST["f_name"]."', '".$_POST["l_name"]."', '".$_POST["email"]."', '".$_POST["admin"]."')";

$add_topic_res = mysqli_query($mysqli, $add_topic_sql) or die(mysqli_error($mysqli));



//get the id of the last query

$id = mysqli_insert_id($mysqli);



//close connection to MySQL

mysqli_close($mysqli);



//create nice message for user

$display_block = "<P>The User <strong>".$_POST["username"]."</strong> has been created.</p>";

?>
[/php]

I would be greatfull if someone could maybe point me in the right direction of what to put under line 12 - //check if username exists

At the moment if i was to have this live i would have people being able to pose as other people rather easily.

cheers for any and all help.

---

### Post by michaelzap on 2009-12-16
Whoa! Danger, Will Robinson! You don't appear to be doing any sort of input validation on your POST vars before inserting them into your database query. This is basically allowing hackers to take over your system without even working at it. You always have to validate any user input before using it.

Basically all that you need to do to check whether a username or email has already been entered into the database is do a query for data matching what the user is inputing and see if there were any records found with matching info. If one or more row was found, then you know that info has already been used (you'd probably want to do two separate select queries - one for username and one for email - so that you can provide the user with a helpful error message for both cases).

Take a look at this page for more complete info:
[http://php.net/manual/en/function.mysql-num-rows.php](http://php.net/manual/en/function.mysql-num-rows.php)

---

### Post by falconindy on 2009-12-16
[img]http://imgs.xkcd.com/comics/exploits_of_a_mom.png[/img]

---

### Post by michaelzap on 2009-12-16
> **falconindy said:**
> [img]http://imgs.xkcd.com/comics/exploits_of_a_mom.png[/img]

I love that strip!

---

### Post by Hellkeepa on 2009-12-17
HELLo!

I've taken the liberty of rewriting the script, to be slightly more secure:
[http://pastebin.com/f1d975409](http://pastebin.com/f1d975409)
I've added the steps necessary for checking for previous users in the comments, and it should be easy enough to figure out how to do it from there.

Also, you'll find the funtions for the "validate.php" file here: [http://norskwebforum.no/pastebin/7609](http://norskwebforum.no/pastebin/7609)
The "quote_smart()" function was taken from this thread: [http://norskwebforum.no/viewtopic.php?p=243716](http://norskwebforum.no/viewtopic.php?p=243716)

Happy codin'

---

### Post by gillespiea on 2009-12-17
waw! i did not expect you guys to go to this much effort! thanks so much!
I did know about my security problems, that was next on the list hehe. Although thanks for the comic, was amusing.

Hellkeepa you're a star mate, thanks for the time you put into it!

---

### Post by denago on 2009-12-17
I'd recommend going with [adodb](http://adodb.sourceforge.net/) for your database access as well.  It will make alot of things easier on you.

---


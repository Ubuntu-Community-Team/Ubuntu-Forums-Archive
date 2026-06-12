---
title: "PHP - Need help designing a login script for a website"
date: 2010-01-21
forum: Programming Talk
---

### Post by teward on 2010-01-21
Title says it all.

Details: I need the PHP page to be able to reference a MySQL database containing a table with a list of authorized usernames and passwords.  If the username and/or passwords don't match any authorized usernames/passwords, the script/page says "there was an error" and to try again.

Anyone know what I need to write in a .php file to make this work?  NOTE: I have an internet site that works and is compatible with php, so don't worry about that.

---

### Post by korvirlol on 2010-01-21
You will have to authenticate your users from your table. 

Based on your authentication working or not, the typical way to go about this is to setup session variables for logged in users.

[http://php.net/manual/en/features.sessions.php](http://php.net/manual/en/features.sessions.php)

---

### Post by heamaster on 2010-01-21
To be honest, Im drunk right now, but I'll try to explain my experience with this anyway even if its good to practice documentation reading. ..

In the top of the .phpfile you need:
[PHP]session_start();[/PHP]
To kinda init the session ...
Then I hope you have constructed a html-form yourself with submit button and everything so you'll have the user and password in $_POST variables ..

anyway you can check if the user have posted login information like this:

[PHP]
if(isset($_POST['user']) && isset($_POST['password'])){
[/PHP]

Then you need to check if it's correct. If you want it to be secure (I assume you want but i wont say more than mysql_escape_string).
Ok, so the user wants to try to login with this information. Simply create/update some "session"-variables. This will be "global" throughout the whole session, or the time the user is visiting your site. Ok, so just do like this:

[PHP]
$_SESSION['user'] = $_POST['user'];
$_SESSION['password'] = $_POST['password'];
}
[/PHP]

Test it as easy as this (note that this test will take place even if the user did not post anything, and then the "old" session variables will be used:

[PHP]$q="Select * from users where username='".$_SESSION['user']."' and password ='".$_SESSION['password']."'";
mysql_query($q);
[/PHP]

Ok now we wanna test if it matched anything:

[PHP]
if(mysql_num_rows() > 0){
$LOGGED_IN = true;
[/PHP]

We do this by cheching if it matched more than 0 entries in MySQL. Ok, so it matched, then we are logged in. Its pretty neat to declare and define a variable named $LOGGED_IN if you want to see if the user is logged in in some other test. Anyway you are logged in, so now you know it.

So if you want some info to only be avalible to logged in users then do simply like this:
[PHP]
if($LOGGED_IN){
print("yeah, logged inxD");
}
[/PHP]

dont forget to add session_destroy(); when you want the user to be logged out!

Sorry everyone if this post seems useless and if I may have missed some parts... As I mentioned before Im drunk right now ... :)

---

### Post by smo0th on 2010-01-21
nice post to be drunk xD

---

### Post by teward on 2010-01-21
alright, after my webserver receives its updates (it'll take time), I'll implement this.  I'll get back to you all.  Thanks!

---

### Post by Ahriman on 2010-01-21
You might also want some anti-Injection code in there, too, before you take it to a production site.
Otherwise, someone could put as their username
```
random' OR 1=1;--
```
or some such, and bam! they have logged in, or worse, they could add in 'DROP tables users' ...
[http://xkcd.com/327/](http://xkcd.com/327/)

---

### Post by Hellkeepa on 2010-01-21
HELLo!

I would like to point out that while the post is quite good, and covers the basics, there is one major thing that's missing from it: Security.

In short:
[list=1][*]Always validate input, to make sure it's within expected parameters. Discard it, and show error messages to the user if it isn't. Make sure you repopulate the form when displaying it again, after validating the rest of the input; Annoying when you have to retype everything.
[*]Always escape output, to avoid XSS and SQL-injections. In the example above the input from the form is passed straight through, and into the database query. 
I refer you to a previous post I made with an example of [SQL security](http://ubuntuforums.org/showpost.php?p=8641992&postcount=7).
[*]Always regenerate the session ID after confirming a successful login, otherwise you're a prime target for session fixating.
[*]Use "header ('Location');" after (successfully) processing data from a form, this'll prevent the form-data from being re-send if the user presses F5.[/list]
Happy codin'!

---


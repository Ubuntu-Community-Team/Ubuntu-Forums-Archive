---
title: "PHP and MySql Authenication (Part 2)"
date: 2007-08-02
forum: Programming Talk
---

### Post by dhtseany on 2007-08-02
Part 1:
[http://ubuntuforums.org/showthread.php?t=514267](http://ubuntuforums.org/showthread.php?t=514267)

Part 2:

Now that I got "Part 1" taken care of, 2 questions:

a) How do I make a universal "[Username] | Logout" deal that appears on every page that requires this authentication?

b) How do carry that authentication from the initial login onto other pages?

If anyone knows of examples, tutorials, etc. that would be super:)
Thanks all!

Sean

---

### Post by bobbocanfly on 2007-08-02
Carrying authentication from one page to another = Cookies. Dead easy. Just checking whether they have them and if they dont tell them to log in.

If you put their username in the cookie, just read that back out then print it onto the page followed by logout link which deletes all the cookies and sends the back to the index.

---

### Post by dhtseany on 2007-08-02
Is it considered good practice to just put the initial authentication scripts on one page (auth.php) and then insert the following onto all the other pages I require authentication on?

```

<?php

include('auth.php')

?>

```

After fiddling around with my scripts for a little bit, I've found doing this works but I'm not sure if this is the way it should be done.

As far as logging out, I'm still fuzzy on how to do that.

Thanks for your help.

---

### Post by smartbei on 2007-08-03
Hello Again :).

Yes, it is considered good practice to include the auth.php page at the top of all the pages that require authentication, at least as far as I have read.

As for printout out username and logout, you already have the username in $_SERVER['PHP_AUTH_USER'], so you can just echo that - much simpler than cookies.

The authentication should already carry itself from what I understand of http authentication. As for loging out, you would use:
```

header('HTTP/1.0 401 Unauthorized');

```
And pobably redirect the user to the homepage using:
```

header('Location: http://www.example.com/');

```

I am not 100% sure about all this, as I have never really created a website that uses http authentication, so try it and see if it works.

---

### Post by dhtseany on 2007-08-03
I created a page called "logout.php" and linked to it from a page that contains the authenticated session. When I click on the link the redirect seems to work but if I click back on the secure link instead of asking for the un/pass again it just takes me straight back to the page, which tells me the session isn't actually killed. Did I do something wrong on the logout code?

**logout.php:**
```

<?php
header('HTTP/1.0 401 Unauthorized');
header('Location: http://www.lakecs.net');
?>

```

Thanks, 

Sean

---

### Post by smartbei on 2007-08-03
I just read a bit about http authentication. Apparently, there is no consistent way to log out of  a session. In light of this, perhaps you should consider switching to a session or cookie based authentication solutiion.  If someone notices I missed something, please correct me.

If you do decide to switch, you can use most (nearly all really) of the same code from the previous thread, with the main difference being that you will have to have a login.php page.

I'd be happy to provide help if you need any with this.

---

### Post by dhtseany on 2007-08-03
Well, I'm not against the idea of cookies, you already know what I'm looking for. Basically, once the user is authenticated I just want to provide the ability to log out. How we have everything else is great other than the lack of a way to kill the session / logout. I already have the login.php page that includes('auth.php') which is where the authentication code is stored. 

So what is your suggestion?

---

### Post by jay019 on 2007-08-03
i'd suggest looking at sessions. i am using these at the moment and they work a treat. check out tizag.com/phpT/phpsessions.php to start with.

but basically, when someone logs in store a session variable...
```

session_start();
$_SESSION[auth]=='true';

```

then using isset you can check if someone is logged in...
```

if (isset($_SESSION[auth]))
{
   // do stuff here
}

``` 

 then when they are all done just...
```

session_destroy();

```

I'm currently using sessions for a shopping cart app which suports two languages.

---

### Post by dhtseany on 2007-08-03
Yeah but will the whole sessions thing work with my current setup? Right now it's checking the username against the mysql database and either allowing or denying the combo. 

The only way I've found to kill the session is firefox can clear all authenticated sessions and that works but nowhere good enough to rely on.

---

### Post by jay019 on 2007-08-03
I take a username and password, check them with the database and then set a session variable that indicates the user has loged in (their usernumber). My logout link just clears the session using session_destroy();

Sent a pm so you can try mine site with sessions and auth.

---

### Post by smartbei on 2007-08-04
Ok, here we go...It turned out to be a little more than a minor refactoring of the code, but...

```

<?php
session_start();
if (isset($_SESSION['userName'])) {
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','password') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_SESSION['userName']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `users` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if ($_SESSION['passwordHash'] != $row['userPass']) {
				//incorrect authentication information found in the session data - password was wrong.
				session_destroy();
				echo "Incorrect authentication information."
		}
	}else {
		//incorrect authentication information found in the session data - username was wrong.
		session_destroy();
		echo "Incorrect authentication information.";
	}
}elseif (isset($_POST['username'])) {
	// Check username and password agains the database.
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','password') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_POST['username']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `users` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if (sha1($_POST['password'] . $row['userSalt']) == $row['userPass']) {
			//user has supplied valid credentials, we set the session with his information.
			$_SESSION['userName']=$_POST['username'];
			$_SESSION['passwordHash']=$row['userPass'];
			$_SESSION['userID']=$row['id'];
		}else {
			//user supplied wrong/invalid login information - password.
			session_destroy();
			echo "Incorrect login information."
		}
			
	}else {
		//user supplied wrong/invalid login information - username.
		session_destroy();
		echo "Incorrect login information."
	}
}
// Following code will be displayed to unauthroized users - it is the form for submitting username and password.
if (!isset($_SESSION['userName'])) {
?>
<form action="" method="post">
<table>
<tr><td>Username:</td><td><input type="text" name="username" id="username" /></td></tr>
<tr><td>Password:</td><td><input type="pass" name="password" id="username" /></td></tr>
<tr><td colspan="2"><input type="submit" value="Login" /></td></tr>
</table>
</form>
<?php
}
exit;
?>

```

You should be able to just include that like you did with the other file. Make sure to insert the correct MySQL database password. By the way - just thought of this - you really should be using 'require' instead of 'include'. Same syntax, just change the word. Reason being that if for some reason php can't access a file referenced with an include statement, it throws a warning and continues processing the page, showing unauthenticated users sensitive data. A require stops the processing of the page.

For displaying username and logout:
Create a new logout.php page with the following code:
```

<?php
session_start();
session_destroy();
header("Location: AFTER_LOGGING_OUT_GO_HERE");
?>

```
You can just link to it to log the user out.

For displaying the username:
```

<?php
if (isset($_SESSION['userName'])) {
	echo $_SESSION['userName'];
}
?>

```

---

### Post by dhtseany on 2007-08-05
Smartbei, you've done it again :)

Alright, so I believe I have only one last question:

I understand now how to echo the username if the user has been authenticated, but what if the user is not authenticated? How I make it so if the user isn't authenticated a link to login would display? I would like to carry the user authentication to pages that are not secure. (You know, like when you visit this forum? Throughout these pages you can still read all pages but instead of echoing the logged in username it will echo the link for logging in.)

I'm starting to understand how **if** statements work, but not 100%. I believe it would be layed out like this::

```

<?php
if (isset($_SESSION['userName'])) {
	echo $_SESSION['userName'];}
        else {echo "<a href='login.php'>Login</a>";}
?>

```

Obviously I tried that code already but it only works if I **require(login.php)** which will requre the auth. on pages i don't require to be logged in otherwise it just displays the login link.

Any ideas?

Thanks

---

### Post by dhtseany on 2007-08-05
Actually I lied, the **require()** isn't working. 

Whenever I refresh a page, it displays this:

```

Warning: mysql_connect(): Access denied for user 'dbconnectlcs'@'p3slh067.shr.phx3.secureserver.net' (using password: YES) in /home/content/l/a/k/lakecs/html/secure/index.php on line 5
Couldn't connect to the database.

```

You can try it out with 1234/password.

Sean

---

### Post by smartbei on 2007-08-06
That looks like a MySQL error, shouldn't have anything to do with the require.

Here is what you should do. Take out the session_start(); command from login.php, and put it right above the place where you require login.php. Then, also stick it at the very top of every other php page you have. Now, you will have access to the $_SESSION variable even on pages that don't require authentication.

---

### Post by dhtseany on 2007-08-06
Hey, first I'd like to thank you for all the continued support.

Second, that was my solution for displaying the username | logout / login problem. It works great! However, I believe my last problem is now designating certains pages as secured. For example, on my website ([www.lakecs.net](www.lakecs.net)) the Downloads section will be considered a secured page. I tried putting the following code at the beginning of the page:

```

//This is the secured download page.
	//Secured Script//
	session_start();
	require('../secure/index.php');

```

When I'm not logged in and click on the Downloads link, the correct username/password boxes pop up. If I put in the correct un/pass combo it then correctly redirects me to the main page where the username is correctly echo'ed. However, if I then try navigating back to the downloads section after correctly logged in it is still spitting out the access denied php/mysql connect error. Am I doing my code for the secured pages wrong?

Thanks for all the help!

Sean

---

### Post by smartbei on 2007-08-07
Well, it might be a cache problem - try refreshing the page. Otherwise, sticking:
```

print_r($_SESSION);

```
right above the place in my php code where it says:
```

if (!isset($_SESSION['userName'])) {

```
And post the results when you do the same thing.
Does this happen on all the authentication-required pages?

Hope this helps.

---

### Post by dhtseany on 2007-08-07
Nope just added onto the problem I was already getting. Check out the screen shots and code:

[[IMG]http://img466.imageshack.us/img466/1423/array1se8.th.jpg[/IMG]](http://img466.imageshack.us/my.php?image=array1se8.jpg)[[IMG]http://img504.imageshack.us/img504/4816/array2mg2.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=array2mg2.jpg)[[IMG]http://img504.imageshack.us/img504/9261/array3ud8.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=array3ud8.jpg)

**/secure/index.php:**
```

<?php

session_start();
print_r($_SESSION);
if (isset($_SESSION['userName'])) {
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','my_password ') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_SESSION['userName']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `user` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if ($_SESSION['passwordHash'] != $row['userPass']) {
				//incorrect authentication information found in the session data - password was wrong.
				session_destroy();
				echo "Incorrect authentication information.";
		}
	}else {
		//incorrect authentication information found in the session data - username was wrong.
		session_destroy();
		echo "Incorrect authentication information.";
	}
}elseif (isset($_POST['username'])) {
	// Check username and password agains the database.
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','my_password') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_POST['username']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `user` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if (sha1($_POST['password'] . $row['userSalt']) == $row['userPass']) {
			//user has supplied valid credentials, we set the session with his information.
			$_SESSION['userName']=$_POST['username'];
			$_SESSION['passwordHash']=$row['userPass'];
			$_SESSION['userID']=$row['id'];
			if (isset($_SESSION['userName'])) {
				header("Location: http://www.lakecs.net/");
}
		}else {
			//user supplied wrong/invalid login information - password.
			session_destroy();
			echo "You're an idiot. You supplied bad login information.";
		}
			
	}else {
		//user supplied wrong/invalid login information - username.
		session_destroy();
		echo "Incorrect login information.";
	}
}
// Following code will be displayed to unauthroized users - it is the form for submitting username and password.
include('../include/1.php');
if (!isset($_SESSION['userName'])) {
echo "
<p/>
<p/>
<form action=\"\" method=\"post\">
The page you requested requires authentication. Please log in:<br/>
<table>
<tr><td>Username:</td><td><input type=\"text\" name=\"username\" id=\"username\" /></td></tr>
<tr><td>Password:</td><td><input type=password name=\"password\" id=\"username\" /></td></tr>
<tr><td colspan=\"2\"><input type=\"submit\" value=\"Login\" /></td></tr>
</table>
</form>
";
}
include('../include/2.php');
exit;
?>

```

**Code for /dl/index.php (intended to be secured)**
```

<?php
//This is the secured download page.
	//Secured Script//
	session_start();
	require('../secure/index.php');
		
	
	//Includes//
	include('../include/1.php');
	
	echo "
	<p/>
	<p/>
	<h3>This is the secured download page. Actual content will be uploaded shortly.</h3>
	
	";
	//Includes//
	include('../include/2.php');
?>

```

You can try it for yourself:
User: testuser
Pass: testpass

As usual, thanks for taking the time to help!

Sean

**UPDATE:**
I forgot to answer your question about other pages. Quick answer: Yes, it's doing it on other pages too. Longer answer: I tried putting the require() on other pages as well and it still didn't work. Those pages also have the session_start(); on them as well.

---

### Post by smartbei on 2007-08-08
Well, when I try using:
User: testuser
Pass: testpass
It seems to work fine, except that the downloads pages isn't protected - Did you change anything?

There is a mistake (not sure if it is the problem or not...) . session_start(); should not be present in /secure/index.php. It should be placed in all of your php files, whether you want authentication on them or not.

Another thing: Your third screenshot shows a MySQL error, not a php one...no idea why it is caused.

Lastly, I meant for you to stick the print_r($_SESSION); right before your:
```

if (!isset($_SESSION['userName'])) {
echo "
<p/>
<p/>

```

And I just noticed - <p/> are not valid html tags. If you want a space, use <br/> If you want a new paragraph, enclose the paragraph in <p> and </p>.

---

### Post by dhtseany on 2007-08-08
**UPDATE:**
Let me rephrase this: The mysql_connect(); error has gone away but now it's not showing me as logged in. It will accept the password, redirect me but no longer echo's the username/logout and still won't let me into the secured downloads section, just keeps asking for the password. Any ideas?

=============

I removed **session_start();** from secure/index.php and made sure  that I placed the **print_r($_SESSION);** code in the correct spot; still getting the error.

Thanks for helping me out.

AHHH!!! This is the last piece to the puzzle for my site and it's starting to drive me nuts!

Thanks for helping

Sean

---

### Post by Wybiral on 2007-08-08
> **dhtseany said:**
> **UPDATE:**
Let me rephrase this: The mysql_connect(); error has gone away but now it's not showing me as logged in. It will accept the password, redirect me but no longer echo's the username/logout and still won't let me into the secured downloads section, just keeps asking for the password. Any ideas?

=============

I removed **session_start();** from secure/index.php and made sure  that I placed the **print_r($_SESSION);** code in the correct spot; still getting the error.

Thanks for helping me out.

AHHH!!! This is the last piece to the puzzle for my site and it's starting to drive me nuts!

Thanks for helping

Sean

I notice it says "Array()" at the top of the login page which is a pretty good indication that something in the PHP script isn't right (assuming, of course, you don't want your page to say array on top).

---

### Post by dhtseany on 2007-08-08
Well, got any suggestions on how to fix it?

Sean

---

### Post by Wybiral on 2007-08-08
> **dhtseany said:**
> Well, got any suggestions on how to fix it?

Sean

Not without some some source code :)

---

### Post by dhtseany on 2007-08-08
**/secure/index.php:**
```

<?php

session_start();
print_r($_SESSION);
if (isset($_SESSION['userName'])) {
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','my_password ') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_SESSION['userName']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `user` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if ($_SESSION['passwordHash'] != $row['userPass']) {
				//incorrect authentication information found in the session data - password was wrong.
				session_destroy();
				echo "Incorrect authentication information.";
		}
	}else {
		//incorrect authentication information found in the session data - username was wrong.
		session_destroy();
		echo "Incorrect authentication information.";
	}
}elseif (isset($_POST['username'])) {
	// Check username and password agains the database.
	$db = mysql_connect('p50mysql13.secureserver.net','dbconnectlcs','my_password') or die("Couldn't connect to the database.");
	mysql_select_db('dbconnectlcs') or die("Couldn't select the database");
	$auth_user = mysql_real_escape_string($_POST['username']);
	$result = mysql_query("SELECT `id`,`userSalt`,`userPass` FROM `user` WHERE `userName`='$auth_user'") or die("Couldn't query the user-database.");
	if (mysql_num_rows($result) == 1) {
		$row=mysql_fetch_assoc($result);
		if (sha1($_POST['password'] . $row['userSalt']) == $row['userPass']) {
			//user has supplied valid credentials, we set the session with his information.
			$_SESSION['userName']=$_POST['username'];
			$_SESSION['passwordHash']=$row['userPass'];
			$_SESSION['userID']=$row['id'];
			if (isset($_SESSION['userName'])) {
				header("Location: http://www.lakecs.net/");
}
		}else {
			//user supplied wrong/invalid login information - password.
			session_destroy();
			echo "You're an idiot. You supplied bad login information.";
		}
			
	}else {
		//user supplied wrong/invalid login information - username.
		session_destroy();
		echo "Incorrect login information.";
	}
}
// Following code will be displayed to unauthroized users - it is the form for submitting username and password.
include('../include/1.php');
if (!isset($_SESSION['userName'])) {
echo "
<p/>
<p/>
<form action=\"\" method=\"post\">
The page you requested requires authentication. Please log in:<br/>
<table>
<tr><td>Username:</td><td><input type=\"text\" name=\"username\" id=\"username\" /></td></tr>
<tr><td>Password:</td><td><input type=password name=\"password\" id=\"username\" /></td></tr>
<tr><td colspan=\"2\"><input type=\"submit\" value=\"Login\" /></td></tr>
</table>
</form>
";
}
include('../include/2.php');
exit;
?>

```

Each page contains **session_start();** which, from my understanding, is supposed to carry the authentication from page to page. Am I wrong in thinking that?

Sean

---

### Post by dhtseany on 2007-08-08
Does anyone think this has something to do with how I'm deeming the pages "secure"? (ex: **require('../secure/index.php');**)? The reason I ask is because the authentication carries onto other "nonsecure" pages and I know this because once logged in the username is being echo'ed. (Also note that all my pages, including secured, have **session_start();** on them.)

Just a thought..

Sean

---

### Post by smartbei on 2007-08-09
Ok, you keep posting the source code that needs to be corrected with things I mentioned earlier. Is this intentional?

Yes, session_start() does carry the authentication, though if the user is not authenticated, the variable $_SESSION['userName'] won't be set, and he won't be allowed access.

I don't have access to a computer with PHP and a webserver installed right now (I am not at home - and I wont be for the next 2 weeks) so I am sorry I can't be more helpful.

---

### Post by dhtseany on 2007-08-09
Alright, check it out: I've reposted the code a few times in case someone else might see something and go "Hey wait, it's that right there!" So yeah, I've been hoping for a miracle haha. As far as the suggested changes to the code I believe I've done all of them you said. The **print_r($_SESSION);** is now in the correct spot but all it seems to do is a) prevent the session from correctly starting and b) putting **Array()** above my login box. And I'm starting to really believe that the problem here may lay in the code I'm using on pages I want secured (like the download section currently is).

Are you sure that require(''); is what I should be using? Again, it seems to causing some sort of duplicate session which mysql spits back and denies access.

Thanks for helping though

Sean

---

### Post by smartbei on 2007-08-10
I really can't tell what the problem is, especially since I don't have access to PHP here.

There is no difference between an 'include' and a 'require' other than the fact that in case a require fails to find a file, it exits the script, whereas an include merely generates a warning. For authentication purposes, it makes by far more sense to use a 'require'.

When I get back home I will be happy to do more :).

---


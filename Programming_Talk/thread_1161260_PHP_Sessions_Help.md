---
title: "PHP Sessions Help"
date: 2009-05-16
forum: Programming Talk
---

### Post by dhtseany on 2009-05-16
Hey all,
Here I am again, playing with PHP and need a bit of help :)

I'm trying to write my own sessions scripts without just copying and pasting from other peoples tutorials. Anywhoo, I have a MySQL database setup with a table called "secure". It currently has 1 username and md5 password stored: UN: admin PW: pass

I have 2 files, dbconnect.php for universal database connectivity and login.php. Here are the two file's code:

dbconnect.php:
```

<?
$con = mysql_connect("mydatabaseURL", "dbUN", "dbPW") or die(mysql_error());
mysql_select_db('selectedDB', $con) or die(mysql_error());
?>

```

login.php:
```

<?
session_start();
include('dbconnect.php');

$Login=$_POST['Login'];

if($Login){
$username=$_POST['user'];
$md5pass=md5($_POST['pass']);


$result=mysql_query("select * from secure where username='$username' and password='$md5pass'");
if(mysql_num_rows($result)!='0'){
session_register('username');
header("main.php");
exit;}
else
{
echo "Bad username or password. Try again";
}}

?>

<html>
<title>Login Page</title>
<body>
<b>Please login to continue.
<form action="<? echo $PHP_SELF; ?>" method="post">
<table align="left" border="0" cellspacing="0" cellpadding="3">
<tr><td>Username:</td><td><input type="text" name="user" maxlength="30"></td></tr>
<tr><td>Password:</td><td><input type="password" name="pass" maxlength="30"></td></tr>
<tr><td colspan="2" align="right"><input type="submit" name="login" value="Go"></td></tr>
</table>
</form>
</body>
</html>

```

OK, so I had a few problems initially with a couple of PHP errors, but was able to take care of them. The login script appears as it's supposed to but when I put in the UN and PW, I hit submit and it does nothing. No errors, no error message saying "Bad UN or PW".

If someone could help me out and take a peek at my code, that'd be awesome.

Thanks in advance for any help I can get.

Peace
Sean

---

### Post by ajy0852 on 2009-05-16
I'm not positive about this, but I think your submit button should have name="Login" rather than name="login" - try capitalizing the L.

---

### Post by dhtseany on 2009-05-16
> **ajy0852 said:**
> I'm not positive about this, but I think your submit button should have name="Login" rather than name="login" - try capitalizing the L.

Wow. Sometimes it just amazes me how something so small can cause so much headache :) Anyways, thanks for taking the time to have a look.

Peace
Sean

---

### Post by ajy0852 on 2009-05-16
Sometimes it just takes another set of eyes ;)

---

### Post by dhtseany on 2009-05-16
OK, got another question:
I'm trying to take the sessions one step further to keep unauthenticated people from viewing certain pages. When the session is setup, the next step for login.php is to redirect the user to main.php (below). Instead of properly displaying the message "Session is set" like it's supposed to, it appears that my main.php isn't correctly recognizing the previously created session. I know this because I setup a separate page to test if my session was successfully created, and it shows that the session is active.

Again, if someone could take a quick look below that'd be great :)

Peace
Sean

main.php:
```

<?
session_start();
if (!isset($_SESSION['username']) 
	|| $_SESSION['username'] !== true) {

   // not logged in, move to login page
   echo "<meta http-equiv='refresh' content='0;URL=http://cust.lakecs.net/secure/login.php' />";
   echo "Please log in...";
   exit;
}
if (!isset($_SESSION['username'])
   || $_SESSION['username'] !== false) {
echo "
Session is set.
<br /><a href='logout.php'>Kill Session</a>";
}
?>

```

---

### Post by odyniec on 2009-05-16
You better stop using session_register() -- it's deprecated and evil, and it might actually be the cause of your problem. Unless you're using a really outdated version of PHP that has the register_globals directive enabled, registering a global variable with session_register() has no effect (see [http://php.net/manual/en/function.session-register.php](http://php.net/manual/en/function.session-register.php) for more information).

If my diagnosis is correct, then your problem should be solved by replacing this line in login.php:
```
session_register('username');
```

with this:
```
$_SESSION['username'] = $username;
```

---

### Post by dhtseany on 2009-05-16
Hi,
First, thanks for the response.

I read up a bit on the link you provided and honestly it's just been a while since I last set up sessions, so that's why I used the old school session_register();. Per your advice I tried replacing that line but it didn't fix the problem. However, if anything at least I've updated the code to more current standards as it did create the session successfully. 

I think that the problem may lay within main.php, specifically with the **if (!isset($_SESSION['username'])** section(s). By chance do you see anything wrong with that?

Peace
Sean

---

### Post by odyniec on 2009-05-17
> **dhtseany said:**
> I think that the problem may lay within main.php, specifically with the **if (!isset($_SESSION['username'])** section(s). By chance do you see anything wrong with that?

Yes, now I see that there is a problem with your if statements. The first if is:

[PHP]if (!isset($_SESSION['username']) 
	|| $_SESSION['username'] !== true) {[/PHP]

Now, since $_SESSION['username'] is a string, the comparison "$_SESSION['username'] !== true" is satisfied, so your program does the redirection to the login page.

Replace the two ifs with a simpler construct:

[PHP]if (!isset($_SESSION['username'])) {
   // not logged in, move to login page
   echo "<meta http-equiv='refresh' content='0;URL=http://cust.lakecs.net/secure/login.php' />";
   echo "Please log in...";
   exit;
}

echo "
Session is set.
<br /><a href='logout.php'>Kill Session</a>";[/PHP]

So you just need to check if $_SESSION['username'] is set, and redirect to the login page if it's not. When your program goes past the check and doesn't exit, you can safely assume the session is valid (and you don't need the second if statement).

---

### Post by dhtseany on 2009-05-17
Thanks again! I kinda had a feeling I was over-complicating things with the multiple "ifs".

What happened to the "Thanks" button?

Peace
Sean

---


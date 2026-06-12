---
title: "PHP Sessions Question"
date: 2009-05-24
forum: Programming Talk
---

### Post by dhtseany on 2009-05-24
Hi all,
Here is what I'm trying to do:
I've successfully setup a user authentication system using PHP and MySQL. Now, I'd like to take it a step further as I want to also have different user "levels" (ie. admin vs. standard user). The mysql table I setup for authentication has 3 fields in use: username, password, and priv. Currently, priv does nothing. However, in the future I'd like to take that "priv" level (Say 1 being admin, 2 being user, etc.) and set a separate session based on the SQL query.

What I'm running into is that all my previous experience with sessions have been in a "Single Session" setup. First, am I on the right line of thinking by setting up a second session to handle this? If so, how would I call the priv sql field and create a **$_SESSION['priv'] = $priv** type of deal?

Thanks for any help:)

Peace
Sean

PS- The following is working code. I made the section I'm talking about in bold.

```

<?

session_start();
include('include/1.php');
include('dbconnect.php');



$Login=$_POST['Login'];

if($Login){

$username=$_POST['user'];

$md5pass=md5($_POST['pass']);





$result=mysql_query("select * from secure where username='$username' and password='$md5pass'");

if(mysql_num_rows($result)!='0'){

$_SESSION['username'] = $username;
[b]// This is what I'm talking about: How can I make this next line work?
$_SESSION['priv'] = $priv;[/b]
   echo "<meta http-equiv='refresh' content='0;URL=secure/members.php' />";

exit;}

else

{

echo "Bad username or password. Try again";

}}



?>
<b>Please login to continue.</b>

<form action="<? echo $PHP_SELF; ?>" method="post">

Username:<br>
<input type="text" name="user" maxlength="30">
<br>
Password:<br><input type="password" name="pass" maxlength="30">
<br><input type="submit" name="Login" value="Go">
</form>
<?
include('include/2.php');
?>

```

---

### Post by Canuckelhead on 2009-05-24
$_SESSION is an array.. you should be able to put everything you need in it..

$_SESSION['priv']

Or am I misunderstanding your post?

---

### Post by Tibuda on 2009-05-24
I think the only thing is missing is to define the $priv variable.

---

### Post by Canuckelhead on 2009-05-24
Maybe somehting like... 

$row = mysql_fetch_array( $result );
$priv = $row['priv'];

---

### Post by soltanis on 2009-05-24
> **dhtseany said:**
> Hi all,
Here is what I'm trying to do:
I've successfully setup a user authentication system using PHP and MySQL. Now, I'd like to take it a step further as I want to also have different user "levels" (ie. admin vs. standard user).


High-five for two programmers working on the same problem!
=;

---

### Post by dhtseany on 2009-05-24
Hey ya'll, thanks for the responses! 

> 
I think the only thing is missing is to define the $priv variable.


Yeah, that's what I meant, I wasn't sure how to define it.

> 
$row = mysql_fetch_array( $result );
$priv = $row['priv'];


That did it! Thank you! 

> 
High-five for two programmers working on the same problem!


Yeah dude, that's whats up. :) Anyways, my plan was to use the following code to check if a user has the required admin level to access certain functions, however I'm not sure if it will do quite what I'm looking for so if anyone has suggestions as to a method that will work better I'm all for it.
```

if (!isset($_SESSION[priv]) 
	|| $_SESSION[priv] !== '1') {
// Checks if the user has admin privileges (being 1 in the priv field) //
echo "You do not have the required user rights to access this page";
header('location:members.php');
}

```

---

### Post by dhtseany on 2009-05-24
By the way, what ever happened to the thank you button?

---

### Post by dhtseany on 2009-05-24
OK, so I can't remember how to properly use an "elseif" statement. Could someone have a look at my (I'm sure by now) butchered code and tell me what I'm doing wrong :-P

Peace
Sean
```

<?
session_start();
if (!isset($_SESSION['username'])) {
echo "<meta http-equiv='refresh' content='0;URL=login.php' />";
echo "Please log in...";
exit;}
elseif (!isset($_SESSION['priv']) 
	|| $_SESSION['priv'] !== '1') {
echo "You are not authorized to view this page. Please wait.";
echo "<meta http-equiv='refresh' content='2;URL=members.php' />";
} else {
echo "
It's working";}
endif;
?>

```

---

### Post by brad@cwp on 2009-05-26
elseif (!isset($_SESSION['priv']) 
	|| $_SESSION['priv'] !== '1')

not equal to is !=.  not !==

---

### Post by dhtseany on 2009-05-26
Hey,
Thanks for the response. This problem was actually solved but thanks anyways. If anyone else is interested in the outcome you can view the other post here:[http://ubuntuforums.org/showthread.php?t=1169736]("http://ubuntuforums.org/showthread.php?t=1169736")

Peace
Sean

---


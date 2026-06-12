---
title: "MySQL Insert Query Error"
date: 2007-08-06
forum: Programming Talk
---

### Post by dhtseany on 2007-08-06
Hi all,

here is another one I'm sure is really easy:) I need to include sha1 with using the INSERT query below. However, from what I've read the syntax is correct although instead of inserting the desired password + sha1 it is inserting the password as sha1(test) (where test is the password is chose). Anyone see what I'm doing wrong?

Thanks in advance for the help

Sean

```

<?php

include "add_cc.php";

if(isset($_POST['submit']))

{

	$FirstName=$_POST['FirstName'];

	$lastname=$_POST['lastname'];
	
	$username=$_POST['username'];
	
	$userpass=$_POST['userpass'];
	
	$usersalt=$_POST['usersalt'];
	
	$coname=$_POST['coname'];
	
	$priphone=$_POST['priphone'];
	
	$email=$_POST['email'];
	
	$addr=$_POST['addr'];
	
	$city=$_POST['city'];
	
	$state=$_POST['state'];
	
	$zip=$_POST['zip'];

  if(strlen($FirstName)<1)

  {
	include('../include/1.php');
      print "Put in their first name and try again.";
	include('../include/2.php');
  }

  else if(strlen($lastname)<1)

  {
	include('../include/1.php');
      print "Fix their last name and try again.";
	include('../include/2.php');
  }

  else

  {
    $insertbutton="INSERT into `user` (coname, firstname, lastname, username, priphone, email, addr, city, state, zip, userpass, usersalt) values ( '$coname','$FirstName','$lastname','$username','$priphone','$email','$addr','$city','$state','$zip','sha1($userpass)','$usersalt')";

    mysql_query($insertbutton) or die(mysql_error());
	
	include('../include/1.php');
    print "Success.";
	include('../include/2.php');
  }



}

else

{
	include('../include/1.php');
	echo "

	<form action='add.php' method='post'>
		<div align='center'>
	<table width='507' border='0'>
		<tr>
		&nbsp;
		</tr>
  		<tr>
  		  <td colspan='2'><div align='center'>Personal Information </div></td>
  		  <td colspan='2'><div align='center'>Account Information </div></td>
	  </tr>
  		<tr>
    		<td width='134'>Company Name:</td>
   		  <td width='120'><input type='text' name='coname' size='20'></td>
  		  <td width='115'>Desired username:</td>
  		  <td width='120'><input type='text' name='username' size='20'></td>
  		</tr>
		<tr>
		  <td>Primary Phone: </td>
		  <td><input name='priphone' type='text' id='priphone' size='20'></td>
		  <td>Desired Password:</td>
		  <td><input type='text' name='userpass' size='20'></td>
	  </tr>
		<tr>
			<td>First Name:</td>
			<td><input type='text' name='FirstName' size='20'></td>
		    <td>Encryption Key:</td>
		    <td><input type='text' name='usersalt' size='20'></td>
		</tr>
		<tr>
			<td>Last Name:</td>
			<td><input type='text' name='lastname' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
  		<tr>
			<td>User's E-mail:</td>
			<td><input type='text' name='email' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
  		</tr>
		<tr>
    		<td>Company's Address:</td>
    		<td><input type='text' name='addr' size='20'></td>
  		    <td>&nbsp;</td>
  		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>City:</td>
			<td><input type='text' name='city' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>State:</td>
			<td><input type='text' name='state' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>Zip:</td>
			<td><input type='text' name='zip' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td></td>
			<td colspan='3'></td>
		</tr>
	</table>
	<input type='submit' name='submit' value='submit'></form>
	</div>
	";

 	include('../include/2.php');

}

?>


```

---

### Post by Wybiral on 2007-08-06
The "sha1($userpass)" shouldn't go in the query.

Try doing it before the query, or just do it when you grab it from $_POST...

Before the query:
```

$userpass = sha1($userpass);

```

OR when you get it from $_POST:
```

$userpass=sha1($_POST['userpass']);

```

EDIT:

I guess you could also concatenate the strings... 

```

$insertbutton = "INSERT into `user` (coname, firstname, lastname, username, priphone, email, addr, city, state, zip, userpass, usersalt) values ( '$coname','$FirstName','$lastname','$username','$priphone','$email','$addr','$city','$state','$zip','".sha1($userpass)."','$usersalt')";

```

But the first two would probably make it easier to find and change if you choose to later.

---

### Post by pmasiar on 2007-08-06
You should *not* use values directly - it is unsafe abd agains "best practices". *Always* use bind variables. There are many examples, dependent on language [1](http://search.cpan.org/~timb/DBI/DBI.pm#execute) [2](http://www.thescripts.com/forum/thread25317.html) [3](http://sqlrelay.sourceforge.net/sqlrelay/programming/perldbi.html)

really, trust me. You dont want some strange values injected into your code, using bind variables will quote them properly.

---

### Post by dhtseany on 2007-08-06
I appreciate the response, thanks:)

The method for adding a user (that I know) is this:

1. Insert the username and password (we'll use 1234) in plain text

2. Select a random salt (We'll use GGHhg%^g)

3. Copy the salt to the end of the password (1234GGHhg%^g) and select sha1. 

Now my question is, how does your method copy that salt to the end of the plain text password before being submitted as sha1?

If I've lost you let me know. Haha remember, I'm a noob so go easy on me :)

Thanks,

Sean

---

### Post by Wybiral on 2007-08-06
Oh, then just use:

```

$userpass=sha1($usersalt.$_POST['userpass']);

```

What pmasiar is saying, I believe, is to NOT use the $_POST data directly, bring it into a variable and use the 'mysql_real_escape_string' I mentioned in your other topic to help avoid injection.

---

### Post by dhtseany on 2007-08-06
I understand what you mean by not directly using the $ things but first I'm focusing on just getting this thing to work. After that, I'm most likely gonna post another thread asking for suggestions on that:)

Anyways, it didn't work. There are no errors or anything popping up; it's just denying the new user which tells me I'm still doing something wrong with my code.

How my code currently looks:

```

<?php

include "add_cc.php";

if(isset($_POST['submit']))

{

	$FirstName=$_POST['FirstName'];

	$lastname=$_POST['lastname'];
	
	$username=$_POST['username'];
	
	$userpass=$_POST['userpass'];
	
//I originally had what you suggested here but I've been messing with it a little//

	$userpass=sha1($_POST['userpass'].$usersalt);
	
	$usersalt=$_POST['usersalt'];
	
	$coname=$_POST['coname'];
	
	$priphone=$_POST['priphone'];
	
	$email=$_POST['email'];
	
	$addr=$_POST['addr'];
	
	$city=$_POST['city'];
	
	$state=$_POST['state'];
	
	$zip=$_POST['zip'];

  if(strlen($FirstName)<1)

  {
	include('../include/1.php');
      print "Put in their first name and try again.";
	include('../include/2.php');
  }

  else if(strlen($lastname)<1)

  {
	include('../include/1.php');
      print "Fix their last name and try again.";
	include('../include/2.php');
  }

  else

  {

    $insertbutton="INSERT into `user` (coname, firstname, lastname, username, priphone, email, addr, city, state, zip, userpass, usersalt) values ( '$coname','$FirstName','$lastname','$username','$priphone','$email','$addr','$city','$state','$zip','$userpass','$usersalt')";

    mysql_query($insertbutton) or die(mysql_error());
	
	include('../include/1.php');
    print "Success.";
	include('../include/2.php');
  }



}

else

{
	include('../include/1.php');
	echo "

	<form action='add.php' method='post'>
		<div align='center'>
	<table width='507' border='0'>
		<tr>
		&nbsp;
		</tr>
  		<tr>
  		  <td colspan='2'><div align='center'>Personal Information </div></td>
  		  <td colspan='2'><div align='center'>Account Information </div></td>
	  </tr>
  		<tr>
    		<td width='134'>Company Name:</td>
   		  <td width='120'><input type='text' name='coname' size='20'></td>
  		  <td width='115'>Desired username:</td>
  		  <td width='120'><input type='text' name='username' size='20'></td>
  		</tr>
		<tr>
		  <td>Primary Phone: </td>
		  <td><input name='priphone' type='text' id='priphone' size='20'></td>
		  <td>Desired Password:</td>
		  <td><input type='text' name='userpass' size='20'></td>
	  </tr>
		<tr>
			<td>First Name:</td>
			<td><input type='text' name='FirstName' size='20'></td>
		    <td>Encryption Key:</td>
		    <td><input type='text' name='usersalt' size='20'></td>
		</tr>
		<tr>
			<td>Last Name:</td>
			<td><input type='text' name='lastname' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
  		<tr>
			<td>User's E-mail:</td>
			<td><input type='text' name='email' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
  		</tr>
		<tr>
    		<td>Company's Address:</td>
    		<td><input type='text' name='addr' size='20'></td>
  		    <td>&nbsp;</td>
  		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>City:</td>
			<td><input type='text' name='city' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>State:</td>
			<td><input type='text' name='state' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td>Zip:</td>
			<td><input type='text' name='zip' size='20'></td>
		    <td>&nbsp;</td>
		    <td>&nbsp;</td>
		</tr>
		<tr>
			<td></td>
			<td colspan='3'></td>
		</tr>
	</table>
	<input type='submit' name='submit' value='submit'></form>
	</div>
	";

 	include('../include/2.php');

}

?>

```

---

### Post by Wybiral on 2007-08-06
You're trying to use "usersalt" before it's declared.

Try:

```

	$usersalt=$_POST['usersalt'];
	$userpass=sha1($_POST['userpass'].$usersalt);

```

If that was the only problem, then it should work.

---

### Post by dhtseany on 2007-08-06
Yep, that was it:)

Thanks for your help!

Sean

---


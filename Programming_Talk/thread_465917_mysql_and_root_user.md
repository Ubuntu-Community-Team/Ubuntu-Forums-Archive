---
title: "mysql and root user"
date: 2007-06-06
forum: Programming Talk
---

### Post by adza on 2007-06-06
Hi there, i want to install a hit counter on my site using php to initialise variable and then call that variable into hit counter etc... The code to do this is realatively simple, however i have a question.. when doing this, should i connect to the database as root? I am a little concerned about this as the current solution i have to connect to my database is ```
$db=mysql_connect("localhost", "root","<myrootpswd>")
``` since i'm inputting my root password here, is this a security risk, can anyone see this?

---

### Post by pbw on 2007-06-06
create a mysql user for the database and use that.

---

### Post by LaRoza on 2007-06-06
> Hi there, i want to install a hit counter on my site using php to initialise variable and then call that variable into hit counter etc... The code to do this is realatively simple, however i have a question.. when doing this, should i connect to the database as root? I am a little concerned about this as the current solution i have to connect to my database is
Code:

$db=mysql_connect("localhost", "root","<myrootpswd>")

since i'm inputting my root password here, is this a security risk, can anyone see this?

You should not connect to the database as root, create a new use with only the neccessary privileges.

Look up the SQL, "GRANT" command, to see the specifics.

---

### Post by adza on 2007-06-08
sweet, thanks ppl :)

---

### Post by adza on 2007-06-09
well... the hit counter is done and now i'm onto the logon script.... however i'm getting an error i can't seem to figure out... ? Hopefully someone here can help me... when i post from my login form to this login script:
```

<?php
//always start the session
session_start();
// check that button has been pressed!
if ((isset($_POST['name'])) && (isset($_POST['pwd'])))
	{
	mysql_connect("localhost", "some_user", "a_password") or die (mysql_error());
	$name=$_POST['name']; //initialise variables
	$pass=$_POST['pwd'];
	$sql="select name 
	      from   works.user
	      where  name='$name'
	      and    pass=PASSWORD('$pass');" ***edit here is the error - found it :) *****
// then the query is executed
	$result=mysql_query($sql) or die (mysql_error());
	if(mysql_num_rows($result)==1)
		{
		//user and pass are correct, increment user visits counter and carry on
		$inc_user="update works.user SET count_logon=(count_logon + 1) where name='$name';" **another one here ****
		mysql_query($inc_user);
		//set the session as connected
		$_SESSION['connected'] = true;
		mysql_close("localhost", "some_user", "a_password");
		echo "<meta http-equiv='refresh' content='0; url=./welcome.php'>";
		exit;
		}
	else
		{
		//user is not validated... send back to index page.
		mysql_close("localhost", "some_user", "a_password");
		echo "<meta http-equiv='refresh' content='0; url=./index.php'>";
		}
	}
else
	{	
	echo "<meta http-equiv='refresh' content='0; url=./index.php'>";
	exit; 
	}
?>

```

I get this error.... > Parse error: syntax error, unexpected T_VARIABLE in /var/www/login.php on line 15 which relates to the $result variable... what am i missing? i've been tearing my hair out for a while here.... :P

---


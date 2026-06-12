---
title: "Stupid PHP Error"
date: 2007-08-21
forum: Programming Talk
---

### Post by dhtseany on 2007-08-21
The FireFox Error:

Warning: mysql_fetch_row(): supplied argument is not a valid MySQL result resource in /home/content/l/a/k/lakecs/html/secure/index.php on line 14
Access Denied: Invalid Credentials.

The Code:
```

<?php
/* get the incoming ID and password hash */
$user = $_POST["userid"];
$pass = sha1($_POST["password"]);

/* establish a connection with the database */
$server = mysql_connect('p50mysql13.secureserver.net', 'dbconnectlcs', 'my_password');
if (!$server) die(mysql_error());
mysql_select_db("dbconnectlcs");

$query = "SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'";

if (mysql_fetch_row($result))
  echo "Access Granted: Welcome, $user!";
else
  echo "Access Denied: Invalid Credentials.";

  ?>
  
  <form action="index.php" method="post">
  <label for="userid">ID</label>
  <input type="text" name="userid" id="userid" />
  <br />
  <label for="password">Password</label>
  <input type="password" name="password" id="password" />
  <br />
  <input type="submit" name="submit" value="Submit" />
</form>

```

I believe that the **if (mysql_fetch_row($result))** line is causing the problem but I'm not 100%. Any suggestions?

Seam

---

### Post by LaRoza on 2007-08-21
> **dhtseany said:**
> The FireFox Error:

Warning: mysql_fetch_row(): supplied argument is not a valid MySQL result resource in /home/content/l/a/k/lakecs/html/secure/index.php on line 14
Access Denied: Invalid Credentials.

The Code:
```

<?php
/* get the incoming ID and password hash */
$user = $_POST["userid"];
$pass = sha1($_POST["password"]);

$server = mysql_connect('p50mysql13.secureserver.net', 'dbconnectlcs', 'my_password');
if (!$server) die(mysql_error());
mysql_select_db("dbconnectlcs");

$query = "SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'";

if (mysql_fetch_row($result))
  echo "Access Granted: Welcome, $user!";
else
  echo "Access Denied: Invalid Credentials.";


```

$result is never defined.

---

### Post by dhtseany on 2007-08-21
So with the way I have the **if (mysql_fetch_row($result));** setup, would it be more practical to replace **$result** with **$query**?

---

### Post by diggity on 2007-08-21
You have to run the query before you can fetch the rows.

$result = **mysql_query**($query);
if(mysql_fetch_row($result))

---

### Post by rock freak on 2007-08-22
So it should look like this. As LaRoza said $result had never been defined!
```

<?php
/* get the incoming ID and password hash */
$user = $_POST["userid"];
$pass = sha1($_POST["password"]);

/* establish a connection with the database */
$server = mysql_connect('p50mysql13.secureserver.net', 'dbconnectlcs', 'my_password');
if (!$server) die(mysql_error());
mysql_select_db("dbconnectlcs");

$query = "SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'";
/* This runs the query that you made above.  From this you can then run mysql_fetch_row */
[COLOR="Red"]$results = mysql_query($query);[/COLOR]

if (mysql_fetch_row($result))
  echo "Access Granted: Welcome, $user!";
else
  echo "Access Denied: Invalid Credentials.";

  ?>
  
  <form action="index.php" method="post">
  <label for="userid">ID</label>
  <input type="text" name="userid" id="userid" />
  <br />
  <label for="password">Password</label>
  <input type="password" name="password" id="password" />
  <br />
  <input type="submit" name="submit" value="Submit" />
</form>

```

---

### Post by dhtseany on 2007-08-22
Please don't think that I'm ungrateful or that I want you to just write the code for me, but that didn't work.

Check it out: [www.lakecs.net](www.lakecs.net) and click on login.

un: test
pw: test

It never accepts the password. Also, I know that mysql is setup correctly so I'm sure thats not the issue.

Thanks,

Sean

---

### Post by LaRoza on 2007-08-22
...edit...

---

### Post by LaRoza on 2007-08-22
The above "corrected" code, uses two different variables, $result and $results, make sure you code is valid.

---

### Post by dhtseany on 2007-08-22
Yeah I noticed that earlier and I took care of that. However, after I removed the single quotes around the variables it started spitting back that original **mysql_fetch_row():** error again. Below is what my code currently reads. 

Thanks for help,
Sean

```

<?php
	$user = $_POST["userid"];
	$pass = sha1($_POST["password"]);

	$server = mysql_connect('p50mysql13.secureserver.net', 'dbconnectlcs', 'my_password');
		if (!$server) die(mysql_error());
		mysql_select_db("dbconnectlcs");

	$query = mysql_query("SELECT * FROM user WHERE Username = $user AND userpass = $pass");

		if (mysql_fetch_row($query))
			echo "Access Granted: Welcome, $user!";
		else
			echo "Access Denied: Invalid Credentials.";
?>
  
  <form action="index.php" method="post">
  <label for="userid">ID</label>
  <input type="text" name="userid" id="userid" />
  <br />
  <label for="password">Password</label>
  <input type="password" name="password" id="password" />
  <br />
  <input type="submit" name="submit" value="Submit" />
  </form>

```

---

### Post by LaRoza on 2007-08-22
I am at school, so I am not able to run and work with the code, but wouldn't it just be easier to extract the values given by the query and test them?

You will need to use mysqli_fetch_array($result), and then compare the values.

Try executing the sql on the command line, to see what is being given, just in case.

---

### Post by diggity on 2007-08-22
It looks like there is a problem with your sql query.

Your code...
"SELECT * FROM user WHERE Username = $user AND userpass = $pass"[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]

Should be...

[/FONT]"SELECT * FROM user WHERE Username = **[COLOR=Red]'[/COLOR]**$user**[COLOR=Red]'[/COLOR] **AND userpass = [COLOR=Red]**'**[/COLOR]$pass**[COLOR=Red]'[/COLOR]** "

You need single quotes around your variables.

BTW, it's a good idea to use mysql_real_escape_string() on your form variables to prevent sql injection attacks and mysql errors.

example: $user = mysql_real_escape_string($_POST['userid']);

---

### Post by aks44 on 2007-08-22
> **dhtseany said:**
> ```
	$user = $_POST["userid"];
	$pass = sha1($_POST["password"]);
[...]
	$query = mysql_query("SELECT * FROM user WHERE Username = $user AND userpass = $pass");

		if (mysql_fetch_row($query))
			echo "Access Granted: Welcome, $user!";
		else
			echo "Access Denied: Invalid Credentials.";
```

Your query may be vulnerable to SQL injection, through the userid POST variable (the password variable is secure in this very case since you hash it beforehand).

Take the good habit of always surrounding your variables in SQL code by single-quotes, and escape the variables with mysql_real_escape_string. [EDIT: diggity you beat me to it]


Something along the lines:

```

$sql = sprintf("SELECT * FROM user WHERE username='%s' AND userpass='%s'",
               mysql_real_escape_string($user),
               mysql_real_escape_string($pass)
              );
$query = mysql_query($sql);
```


Also, whenever you output a variable to the HTML page (ie. **echo "Access Granted: Welcome, *$user*!";**), you should escape it with htmlspecialchars to prevent HTML / JavaScript injections.

eg.

```
echo "Access Granted: Welcome, ".htmlspecialchars($user)."!";
```

---

### Post by dhtseany on 2007-08-22
Ok I've been messing around with the CLI for a little bit now and here is the command I've been using:

```

select * from user where username = 'test' and userpass = sha1('test');

```

There are no result being returned because I'm not including the salt in this table. With that being said, how exactly would this script we're working with incorporate the unique salt for each username? (Edit: Without having the salt present in the PHP script)?

---

### Post by aks44 on 2007-08-22
> **dhtseany said:**
> There are no result being returned because I'm not including the salt in this table. With that being said, how exactly would this script we're working with incorporate the unique salt for each username? (Edit: Without having the salt present in the PHP script)?

What is the supposed meaning of **salt** from your point of view? Because I can't make sense out of your sentences...

The SHA1 algorithm doesn't need any salt value.

---

### Post by dhtseany on 2007-08-22
Ok wow after you questioned me about the salt thing it made me realize that the "salt" meant taking the sha1 and using the salt/random value as the encryption key. Ok so yeah it defiantly works now.

I guess my last question is how do you carry this authentication onto other pages so that i can use **require('../secured/index.php');** and if the user already logged in they won't have to do it again?

---

### Post by aks44 on 2007-08-22
> **dhtseany said:**
> the "salt" meant taking the sha1 and using the salt/random value as the encryption key.
Call me dense on this one, but the "salt/random value" part still doesn't make much sense to me... And what encryption system are you using?

> **dhtseany said:**
> I guess my last question is how do you carry this authentication onto other pages so that i can use **require('../secured/index.php');** and if the user already logged in they won't have to do it again?

This one is easier to answer. :)
Once you validated the login, store the user / password hash combination in some $_SESSION variable (don't forget to call session_start() before doing anything related to sessions).
Whenever a protected page loads, include a script that checks if the $_SESSION variables are set AND if they relate to a valid user. If yes, just go on with the page you were loading, else present the user again with the login form.

---

### Post by dhtseany on 2007-08-22
Ok so I need **session_start();** at the beginning of each page to be deemed secure; I know that much. However, could you give me an example of what you mean for the checking if everything is valid part? :)

Thanks

---

### Post by aks44 on 2007-08-22
In your login script (the one that handles the POST query), use something along the lines :

```
// database stuff here, seems you got it right by now
if ($correct_credentials /* adjust the condition */ )
{
  $_SESSION['user'] = $user;
  $_SESSION['pass'] = $hashed_pass;
}
else
{
  unset($_SESSION['user']);
  unset($_SESSION['pass']);
}
```

In your verification script (the one you will include at the top of every protected page):

```

$logged_in = false;
if (isset($_SESSION['user']) && isset($_SESSION['pass']))
{
  // database stuff again, just don't re-hash the password as it is already hashed in $_SESSION['pass']
  if ($correct_credentials /* adjust the condition */ )
    $logged_in = true;
}
if (!$logged_in)
{
  unset($_SESSION['user']);
  unset($_SESSION['pass']);
  // display your login form
  die;
}
```

It's a rough draft, hope it puts you on the tracks.

---


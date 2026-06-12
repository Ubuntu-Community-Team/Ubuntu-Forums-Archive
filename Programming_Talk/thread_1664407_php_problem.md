---
title: "php problem"
date: 2011-01-10
forum: Programming Talk
---

### Post by cboxhero on 2011-01-10
```
<?php

session_start();

$username = $_POST['        '];
$password = $_POST['         '];


if ($username&&$password)
{

$connect = mysql_connect("         ","          ","         ") or die("Couldn't Connect.");
mysql_select_db("       ") or die ("couldn't find database.");

$query = mysql_query("SELECT * FROM users WHERE username='$username'");

$numrows = mysql_num_rows($query);

if ($numrows!=0)
{

while ($row = mysql_fetch_assoc($query))

{
$dbusername = $row['username'];
$dbpassword = $row['password'];
}

if ($username==$dbusername&&$password==$dbpassword)

{

echo "You are now logged in. <a href='           .php'>Click</a> here to enter our members page.";
$SESSION['username']==$dbusername;

}
else
    echo"a.";

}
else
    echo"b.";
}
else
    die("c.");
?>

```




Is there anything wrong with this?

---

### Post by shadylookin on 2011-01-10
looking at it briefly I don't see any obvious things, what exactly is happening when you run it?


There are some potential safety issues as it appears that you store passwords as plain-text, but I imagine you're not concerned with that at the moment

---

### Post by cipherboy_loc on 2011-01-11
You might be missing a left curly brace for the if statement before the last while loop. Alan, reformat it to look like this:

```

if (condition == true) {
    while ($a != 9) {
        print "$a";
        $a += 1;
    }
}

```

It is much easier to read and follow brackets/braces that way. Just because no-one will see it doesn't mean you can make it look bad. Sloppy code might not execute the way you want it to.


Cipherboy

---

### Post by cboxhero on 2011-01-12
I don't think it is, because when I just use something simple like the code below, the $numrows won't display.

```
<?php

$username = $_POST['username'];
$password = $_POST['username'];

if ($username&&$password)
{

$connect = mysql_connect("     ","   ","     ") or die("Couldn't connect.");
mysql_select_db("         ") or die ("Couldn't find database.");

$query = mysql_query("SELECT * FROM users WHERE username='$username'");

$numrows = mysql_num_rows($query);

echo $numrows;

}
else
    die("Please enter a username and password.");

?>
```

---

### Post by cboxhero on 2011-01-12
Can some one people explain why it's not displaying anything?:confused::confused:

---

### Post by shadylookin on 2011-01-12
your query could be failing and you have warnings/errors turned off.

---

### Post by cboxhero on 2011-01-12
How could I turn on warnings/errors on?

---

### Post by cboxhero on 2011-01-13
I fixed the query ... But there is a problem in the area below. I REALLY NEED HELP!!! [-o< [-o< [-o< [-o< [-o< [-o< [-o<

```
if ($numrows!=0)
{
// Code to log in!

while ($row = mysql_fetch_assoc($query))
{

    $dbusername = $row['username'];
    $dbpassword = $row['password'];


}

// Check to see if they match!
if ($username==$dbusername&&$password==$dbpassword)
{

echo"You're in. Congrats. >.<";


}
else
    die("The provided password is invalid.");

}
else
    die("The provided username is not valid.");
}

```

---

### Post by shadylookin on 2011-01-13
putting 

```
ini_set('error_reporting', E_ALL);
```

at the beginning of your script should work

---

### Post by cboxhero on 2011-01-13
The error reporting didn't work. Anything else?

---

### Post by cboxhero on 2011-01-13
I need a solution soon too. I have to sleep and I have to have this website by tomorrow.

---

### Post by cboxhero on 2011-01-13
I still can't figure it out. I do know it's somewhere around there though. Because every time I'm trying something, the only thing displaying is the "The provided username is invalid."
I hope this helps someone help me.

---

### Post by cboxhero on 2011-01-13
I'm almost positive that I have no problems in my code, but it still won't work.

---

### Post by shadylookin on 2011-01-13
try some more echo statements to see where it's really failing at then. 

```

echo("before row check");
if ($numrows!=0)
{
// Code to log in!
echo("before loop");
while ($row = mysql_fetch_assoc($query))
{

    $dbusername = $row['username'];
    $dbpassword = $row['password'];


}
echo("after loop");
// Check to see if they match!
if ($username==$dbusername&&$password==$dbpassword)
{

echo"You're in. Congrats. >.<";


}
else
    die("The provided password is invalid.");

}
else
    die("The provided username is not valid.");
}

```

Also for what it's worth nested else statements without brackets and indentation are hard to interpret. At first I thought you had to else statements for the same portion.

---

### Post by cboxhero on 2011-01-13
I tried that ... And what I got was, "Before row checkThe provided username is invalid."

So, I'm guessing it's the second if statement. Let me try and fix it.


NOPE! Nothing worked. Is there anything that I can put other then, "if ($numrows!=0)" ?

---

### Post by cboxhero on 2011-01-13
Well ... I'm going to sleep. If you find a solution, by testing it of whatever .... Please post it. I will be checking this in the morning.

---

### Post by cboxhero on 2011-01-13
Well ... I'm going to sleep. If you find a solution, by testing it of whatever .... Please post it. I will be checking this in the morning.

---

### Post by shadylookin on 2011-01-13
post fail

---

### Post by shadylookin on 2011-01-13
post fail again

---

### Post by shadylookin on 2011-01-13
you could try echoing out $numrows and see if it's actually a number. 

if it's not a number then your sql query still has problems.

---

### Post by cboxhero on 2011-01-13
I tried echo out $numrows and it doesn't show anything.

---

### Post by shadylookin on 2011-01-13
then I would check your query specifically with something like this

```

if($query==false){
   echo("error executing query");
}

```

right after this line

$query = mysql_query("SELECT * FROM users WHERE username='$username'");

---


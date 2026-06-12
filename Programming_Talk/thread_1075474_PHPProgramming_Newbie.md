---
title: "PHP/Programming Newbie"
date: 2009-02-20
forum: Programming Talk
---

### Post by mregister on 2009-02-20
Hello All,

I am trying to learn PHP from a book and I am going through an example that I can't get to work. I have gone over it several times and from what I have read I am starting to think that maybe there is a setting in a .ini file somewhere I am missing?
What I am trying to do is have a user login and create a session.

So, the user logs in and $userid and $password are given to the script with a post. The script assigns then checks a mysql db to see if the user is valid:
```
$result = $db_conn->query($query);
if ($result->num_rows > 0)
{
$_SESSSION['valid_user'] = $userid;
}
```

I know the validation works bc I modified the script without trying to create a session and the login works fine I just can't establish a sesssion. I start the script with:

```
session_start();
```

Thanks to all for any advice.

Mark

---

### Post by konqueror7 on 2009-02-20
did you put the *session_start()* method above all html elements?

---

### Post by Reiger on 2009-02-20
Where does $userid get set?

---

### Post by mregister on 2009-02-20
yes session_start() is the very first line. $userid is set from:
```
$userid = $_POST['userid'];
```

---

### Post by konqueror7 on 2009-02-20
is your cookie enabled in your browser? if i remember correctly, sessions works similar to a cookie...

can you perhaps post your html pages, so we can inspect it...

---

### Post by mregister on 2009-02-20
This is the script entirely:

```
<?php

session_start();

if (isset($_POST['userid']) && isset($_POST['password']))
{
    $userid = $_POST['userid'];
    $password = $_POST['password'];
    
    $db_conn = new mysqli(localhost,webauth,webauth,auth);
    
    if (mysqli_connect_errno())
    {
        echo 'Connection to database failed: '.mysqli_connect_error();
        exit();
    }
    
    $query = 'select * from authorized_users '
             ."where name = '$userid' "
             ." and password=sha1 ('$password')";
             
    $result = $db_conn->query($query);
    if ($result->num_row > 0)
    {
        $_SESSION['valid_user'] = $userid;
    }
    $db_conn->close();
    
}

?>

<html>
<body>
<h1>Home Page</h1>
<?
if (isset($_SESSION['valid_user']))
{
    echo 'Your are logged in as: ' .$_SESSION['valid_user'].' <br />';
    echo '<a href="logout.php">Log Out</a><br />';
}

else
{
    if(isset($userid))
    {
        echo 'Could not log you in. <br />';
        
    }
    
    else
    {
        echo 'You have not tried to login. <br />';
    }
    
    echo '<form method="post" action="authmain1.php">';
    echo '<table>';
    echo '<tr><td>Userid:</td>';
    echo '<td><input type="text" name="userid"></td></tr>';
    echo '<tr><td>Password:</td>';
    echo '<td><input type="password" name="password"></td></tr>';
    echo '<tr><td colspan="2 align="center">';
    echo '<input type="submit" value="Log in"></td></tr>';
    echo '</table></form>';
}

?>
<br />
<a href="members_only.php">Members Section</a>
</body>
</html>

```

After trying to sign in the script returns the message "Could Not Log You in" which seems to indicate that the login works but not the session. And as I said, I can get a login to work if I am just doing that but  no session.

---

### Post by konqueror7 on 2009-02-20
it seems that the session hasn't been initialized in the second page...try adding a *session_start()* in the second page(if i remember correctly, that is:))...
also, try putting first an "echo $userid" in your first page, just to make it sure that it does get something...

---

### Post by mregister on 2009-02-20
I added the line suggested by konqueror ```
'You are logged in as: ' .$userid
``` and that does print out the user name. I know the login portion works, it's just the session part that does not work??

---

### Post by konqueror7 on 2009-02-20
have tried adding a *session_start()* in the second page? because you need to initialize a session first...

---

### Post by mregister on 2009-02-20
yes session_start() is at the top. So confusing. The login worked. After I put that echo statment in you suggested it reads "You are logged in as test" which is right, but when I go to the next page it tells me "You are not logged in". This is the code on the 2nd page:
```
<?php
  session_start();
  
  echo '<h1>Members Only</h1>';
  
  // check session variable
  
  if (isset($_SESSION['valid_user']))
  {
      echo '<p>You are logged in as: ' .$_SESSION['valid_user'].'<p>';
      echo '<p>Members only content goes here</p>';
      
  }
  
  else
  {
      echo '<p>You are not logged in.</p>';
      echo '<p>Only logged in members may see this page.</p>';
      
  }
  
  echo '<a href="authmain1.php">Back to Main Page</a>';
  
?>
```

---

### Post by JK3mp on 2009-02-20
possibly validation of the session problem

---

### Post by konqueror7 on 2009-02-20
btw, in my code, its very similar,,,,you stored in your $userid variable is integer (based on the primary key on the db),,,use
```
($_SESSION['valid_user'] != 0)
```

instead, assuming that you don't have an ID of 0...

---

### Post by mregister on 2009-02-20
No the userid is stored as a varchar. I am starting to think it is a cookie issue. Maybe I need to set a cookie to track the session? I added this to the bottom of the first page:
```
$cookie = session_get_cookie_params();

foreach ($cookie as $key => $value)
echo '<br />';
echo  $key . '=> ' .$value. '<br />';
```

to see if anything comes back. And the only thing I get is:

httponly=>

with no value. My browser accepts cookies so I guess I need to setup a cookie in the script?

---

### Post by konqueror7 on 2009-02-20
varchar? trying putting
```
($_SESSION['valid_user'] != "" || isset($_SESSION['valid_user']))
```

---

### Post by mregister on 2009-02-20
I dont' understand. Put that where? The only place that $_SESSION is set is = $userid. 

Maybe I don't understand you suggestion?

---

### Post by konqueror7 on 2009-02-20
in your second page...i also think that maybe the condition is the one that's giving you problems...

---


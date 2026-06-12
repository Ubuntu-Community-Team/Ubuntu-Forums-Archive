---
title: "Simple Login"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by musty202 on 2012-06-14
Hello,

Please i'm trying to create a simple php login page, but i keep getting this error"**Warning**: mysql_result() expects parameter 1 to be resource, boolean given  in **C:\xampp\htdocs\myticket\login.php** on line **15**
Login  Successful. Welcome Backsir/madam.", the login is working, and displays the successful message, comes with error, below is my code


```

<?php

$username = $_POST['username'];
$password = $_POST['password'];
$login = $_GET['login'];


if($login =='yes')
{
    $con = mysql_connect("localhost","root","");
    mysql_select_db("login");
    
    $get = mysql_query("SELECT count(id) FROM login WHERE user='$username' and pass='$password'");
    
    $result = mysql_result($get, 0);
    
    if($result!=0)
    {
        echo "Invalid Login";
        
    }
    else
    {
        echo "Login Successful. Welcome Back".$_COOKIE['username']."sir/madam.";
        $_SESSION['username'] = $username;
    }
    }
?>

```

---


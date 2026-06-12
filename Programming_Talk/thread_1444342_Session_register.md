---
title: "Session register"
date: 2010-04-01
forum: Programming Talk
---

### Post by Maikovich on 2010-04-01
Hello, I've made a log in form.

When everything is filled in well, the session must be registered. But how do I do this and why doesn't this work:

Log in form:
 
[php]<?php

include '../registration/functions.php';

?>

<html>
<head>
<title>Welkom bij Railz!</title>
</head>

<body>

<center>
<form method='POST' action='startrailz.php'>
    <table border='0' style='color: black;
    width: 255px;
    margin-top: 5px;
    border: 1px solid black;
    padding: 2px;
    font-family: Tahoma, Geneva, sans-serif;
    font-size: 12px;'>
    <center>
        <tr>
            <td>
            Gebruikersnaam:
            </td>
            <td>
            <input type='text' name='myusername'>
            </td>
        </tr>
        <tr>
            <td>
            Wachtwoord:
            </td>
            <td>
            <input type='password' name='mypassword'>
            </td>
        </tr>
        <tr>
            <td colspan='2' align='right'>
            <input type='submit' name='submit' value="Log in">
            </td>
        </tr>
    </table>
</form>

<?php

$myusername=addslashes(strip_tags($_POST['myusername']));
$mypassword=addslashes(strip_tags($_POST['mypassword']));

$session_username = addslashes(strip_tags($_SESSION['myusername']));

$login = (mysql_query("SELECT * FROM `$tbl_name` WHERE user='$myusername'"));

if($_POST['submit']) {
?>
<html>
<head>
</head>
<body>
<table border='0' style='color: red;
width: 255px;
margin-top: 5px;
border: 1px solid black;
padding: 2px;
font-family: Tahoma, Geneva, sans-serif;
font-size: 12px;'>
<center>
<?php

if ((!$myusername) || (!$mypassword) || (mysql_num_rows($login) == 0))
    echo "<tr><td>Je gebruikersnaam en/of wachtwoord is niet juist ingevuld.</tr></td>";
            
        else {
            while ($login_row = mysql_fetch_assoc($login)) {
                
                $mypassword_db = $login_row['pass'];
                
                if ($mypassword != $mypassword_db)
                echo "<tr><td>Onjuist wachtwoord.</tr></td>";
                
                else {
                    
                    $myactive = $login_row['active'];
                    $myemailadress_db = $login_row['email'];
                    
                    if ($myactive == 0)
                    echo "<tr><td>Je hebt je account nog niet geactiveerd. Check je(<b>".$myemailadress_db."</b>) om je account te activeren.</tr></td>";
                    
                    else {
                        ($_SESSION['myusername'] = $myusername);
                        header('location:startrailz.php');
                    }
                }
            }
        }
?></center>
<?php
}
?>
</center>
</table>
</body>
</html>[/php]

Page (startrailz.php):

[php]<?php

include '../registration/functions.php';

$myusername=addslashes(strip_tags($_POST['myusername']));

session_start();
if  ($_SESSION['myusername'] !== $myusername); {
    header('location:index.php');
}
    
?>

<html>
<head> 
<title>Welkom bij Railz!</title>
</head>
<body>
<h1>Met succes ingelogd!</h1>

<p>
<a href='../login/logout.php'>Log uit!</a></p>

</body>
</html>[/php]

---

### Post by Maikovich on 2010-04-02
bump

---

### Post by ELD on 2010-04-02
First of all any page that uses the session will need "session_start();" at the very top of the page before you set anything to do with the session.

My pages are started like so
[php]
<?php
session_start();
// all other code below...
[/php]


On the login page you have this:
[php]
($_SESSION['myusername'] = $myusername);
[/php]
Remove the () there is no need for that.

As for using "addslashes(strip_tags(" to sanitize data for the database you should use "mysql_real_escape_string" instead, look it up on php.net. I believe in the comments on that functions page someone posts a "quote_smart" function, take a look.

As to the reason it is not working, on the page "startrailz.php" you are comparing the session username to a forms post username which isn't set as to get to that page you are using a header redirect which will not keep forms post data.

---

### Post by Maikovich on 2010-04-07
I still don't really get what to do. How must it look like to get a clear session start?

---

### Post by Maikovich on 2010-04-07
bump

---

### Post by Maikovich on 2010-04-08
Could nobody help me?

---

### Post by ELD on 2010-04-08
I already told you how to do a clear session start, re-read my post.

---


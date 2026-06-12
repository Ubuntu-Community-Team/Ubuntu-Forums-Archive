---
title: "Login form"
date: 2010-03-30
forum: Programming Talk
---

### Post by Maikovich on 2010-03-30
Hello.

An error occured when I tried to execute this script (the password has been censored).

The error says: 

**Warning**:  mysql_result() expects parameter 1 to be resource,  boolean given in **C:\xampp\htdocs\xampp\test.php** on line **24**

The script is:

[PHP]<?php session_start(); ?>

<html>
<head />
<body>

<form action='test.php?login=yes' method=POST>
Nickname: <input type=text name='user'><br />
Password: <input type=password name='pass'><br />
<input type=submit value="Railz!">
</form>

<?php

    $user=$_POST['user'];
    $pass=$_POST['pass'];
    $login=$_GET['login'];
    
    if ($login=='yes'){
        $con=mysql_connect('localhost', 'Maikovich', '*********');
        mysql_select_db('login');
             
        $get=mysql_query("SELECT count(id) FROM 'users' WHERE user='$user' AND pass='$pass'");
        $result=mysql_result($get, 0);
             
        mysql_close($con);
             
        if ($result!=1) echo "Oeps! Probeer opnieuw.";
        else{
            echo "Je bent ingelogd!";
            $_SESSION['user']=$user;
        };
    };
    
?>    

</body>
</html>[/PHP]
Could you please help me, I'd appreciate it :-)

---

### Post by Compyx on 2010-03-30
You should check the result of mysql_query(), judging from the error message mysql_query() returned false, indicating an error. The error is in your SQL statement: replace the single quotes around 'users' with backticks: `users`.

And consider using something like sprintf() in combination with mysql_real_escape_string() to generate the SQL statement to avoid SQL-injection attacks.

---

### Post by Maikovich on 2010-03-30
Thanks. Now I tried something else which didn't work:

[PHP]<div id='loginform'>

    <form method='post' action='checklogin.php' name='loginform1'>
    <input type='text' value="Gebruikersnaam" name='myusername' id='username' /><br />
    <input type='password' value="Wachtwoord" name='mypassword' id='password' /><br />
    <input type='submit' name='submit' value="Railz!" />[/PHP]The "value" function doesn't work. "Gebruikersnaam" doesn't appear in the text box, while the value function of password DOES work.

---

### Post by Hellkeepa on 2010-03-30
HELLo!

The HTML code you posted should work, if it doesn't then you must have done something wrong in the actual page. Either that, or something really weird is going on.

Once that is said I also recommend using "mysql_real_escape_string ()", or rather **Stadkle**'s "quote_smart ()" function (which I've linked to in several places here), to avoid being targeted by SQL injects. Plus input validation, to make sure the input is within the expected parameters of a login form; Username with null-bytes or ASCII < 32 is usually not a very good sign, for example.
I also, strongly, recommend to use "session_regenerate_id ()" after confirming the username and password, and before saving anything to the $_SESSION array. This prevents session fixation.

Another protip is doing all of the PHP processing before printing out the HTML code, that way you'll have a lot more flexibility when it comes to acting upon the user input. Things like redirecting to the users "home" page, when logging in, or showing an error above the form. That's just the tip of the iceberg.

Happy codin'!

---

### Post by Maikovich on 2010-03-30
Thank you for your reaction. Thanks for the remark.

I will post the whole script:

[PHP]<html>
<head>
<title>Login Page</title>

<style type="text/css">
#loginform {
    border: solid #000 1px;
    background-color: #3CF;
    width: 160px
}

form {
    margin: 5px;
}

label {
    display: block;
    width: 3px;
    float: left;
    clear: left;
}

label, input {
    margin-bottom: 3px;
}
    
</style>
</head>
<body>

<div id='loginform'>

    <form method='post' action='checklogin.php' name='loginform1'>
    <input type='text' value="Gebruikersnaam" name='myusername' class='myusername' id='username' /><br />
    <input type='password' value="Wachtwoord" name='mypassword' class='mypassword' id='password' /><br />
    <input type='submit' name='submit' class='submit' value="Railz!" />

</body>
</html>[/PHP]

The username value just doesn't work.

---

### Post by Compyx on 2010-03-30
Works fine on my system. Have you tried clearing the browser cache or simple refreshing the page?

---

### Post by Maikovich on 2010-03-30
Weird, if I open a new file it works but in my mainlogin.php it doesn't.

---

### Post by Maikovich on 2010-03-30
Sorry for dubbleposting.

Please remove this. :-)

---


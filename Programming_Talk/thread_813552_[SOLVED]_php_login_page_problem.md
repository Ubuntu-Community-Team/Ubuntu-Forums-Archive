---
title: "[SOLVED] php login page problem"
date: 2008-05-30
forum: Programming Talk
---

### Post by Nythain on 2008-05-30
Ok, a little backstory on the situation. Im creating a php login to my ftp server via web browser for those browsers that support it. I successfully set up proftpd to use mysql database for users and passwords and quotalimits, i successfully set up a php page to create a username and password for the ftp server via the web, and i half successfully set up a php login for it.

What it does, checks the mysql database to see if the user exists, if so, checks the password, if so, redirects them in a new window/tab to the ftp server with the and logs them in with the provided username and password.

What its not doing, logging them in on the initial form submission... it just redirects them to a white page in firefox and a server not available at this time page in IE (IE only tested on my girlies laptop, since everyone i know uses firefox).

upon "refreshing" the page and resubmitting post data, it connects and loads the ftp server just fine... upon clickin on the submit button a second, third, etc time it connects and loads just fine... just not on the initial submit.

and now for the code:
```

<?php
// Connects to the database
mysql_connect("XXXXX", "XXXXX", "XXXXX") or die(mysql_error());
mysql_select_db("XXXXX") or die(mysql_error());

//Checks if there is a login cookie
if(isset($_COOKIE['ID_my_site']))
    //if there is, it logs you in and directes you to the members page
    {
    $username = $_COOKIE['ID_my_site'];
    $passwd = $_COOKIE['Key_my_site'];
    $check = mysql_query("SELECT * FROM xxxxx WHERE xxxxx = '$username'")or die(mysql_error());
    while($info = mysql_fetch_array( $check ))
        {
        if ($passwd != $info['xxxxx'])
            {
            }
        else
            {
            header ("Location: ftp://$username:$passwd@xxxxx");
            }
        }
    }

//if the login form is submitted
if (isset($_POST['submit']))
    { // if form has been submitted

      // makes sure they filled it in
        if(!$_POST['username'] | !$_POST['passwd'])
            {
            die('You did not fill in a required field.');
            }

      // checks it against the database
        if (!get_magic_quotes_gpc())
            {
            $_POST['email'] = addslashes($_POST['email']);
            }

        $check = mysql_query("SELECT * FROM xxxxx WHERE xxxxx = '".$_POST['username']."'")or die(mysql_error());
     //Gives error if user dosen't exist
        $check2 = mysql_num_rows($check);

        if ($check2 == 0)
            {
            die('That user does not exist in our database. <a href=xxxxx.php>Click Here to Register</a>');
            }
        while($info = mysql_fetch_array( $check ))
            {
            $_POST['passwd'] = stripslashes($_POST['passwd']);
            $info['xxxxx'] = stripslashes($info['xxxxx']);

            //gives error if the password is wrong
            if ($_POST['passwd'] != $info['xxxxx'])
                {
                die('Incorrect password, please try again.');
                }
            else
                {
                // if login is ok then we add a cookie
                $_POST['username'] = stripslashes($_POST['username']);
                $hour = time() + 3600;
                setcookie(ID_my_site, $_POST['username'], $hour);
                setcookie(Key_my_site, $_POST['passwd'], $hour);

                //then redirect them to the members area
                header ("Location: ftp://$username:$passwd@xxxxx");
                }
            }
    }
else
    {

    // if they are not logged in
    ?>
    <html>
    <head>
    <meta http-equiv='Content-Type' content='text/html; charset=utf-8'/>
    <style type="text/css">
    body { 
        background-color: black; 
    }
    td.chatformtext {
        text-align: left;
        font-size: 10px
        font-family: sans-serif;
        color: #ffffff; 
    }
    input.chatbutton {
        border: 1px solid #448;
        background: #ffffff;
        font-family: sans-serif;
        font-size: 13px;
        color: #222;
    }
    input.chatinput {
        background: white;
        font-family: sans-serif;
        padding: 1px;
        font-size: 13px;
        color: #333;
        border: 1px solid #448;
    }
    </style>
    </head>
    <body onload="init()" onunload="shutdown()">
    <form action="<?php echo $_SERVER['PHP_SELF']?>" method="post" target="_blank">
    <table border="0">
    <tr><td class="chatformtext" colspan=2>Login</td></tr>
    <tr><td class="chatformtext">Username:</td><td>
    <input class="chatinput" type="text" name="username" maxlength="40">
    </td></tr>
    <tr><td class="chatformtext">Password:</td><td>
    <input class="chatinput" type="password" name="passwd" maxlength="50">
    </td></tr>
    <tr><td colspan="2" align="center">
    <input class="chatbutton" type="submit" name="submit" value="Login">
    </td></tr>
    <tr><td colspan="2"><a href="http://xxxxx/xxxxx.php>Not a member? Click here to register.</a></td></tr>
    </table>
    </form>
    </html>
    <?php
    }

?>

```I've xxxxx'd out all the tables, databases, users, passwords and server addresses in an attempt to keep myself a little bit secure here, i know they are all correct because well, it works, just not on the first shot.

any advice, code rewrites, suggestions, ideas, guesses, help, guidance, links, etc are very much appreciated.

---

### Post by Nythain on 2008-05-30
ok, well aparently the only reason it was working on the consecutive tries was because of cookies... commenting out the cookies check and cookies creation = no work at all... just the white page of doom!!!

still stuck here, thanks

---

### Post by henchman on 2008-05-31
Have you tried it with different browsers? It seems as if the browser doesnt like setcookie in combination with header(). You can try to use [output buffering]("http://www.php.net/ob_start") for php

You can also workaround this by using either JavaScript or HTML meta tags for redirecting...

```
window.location.href = "ftp...";
```

or 

```
<meta http-equiv="refresh" content="0; URL=ftp://foobar">
```

---

### Post by Nythain on 2008-05-31
yeah, looks like im gonna have to rely on a meta refresh, thanks for the advice, days of playing around and it works now :)

still curious why the header location didnt work, even after commenting out all the cookies (actually made it work less, with cookies it at least worked on the refreshes)

oh well, the world may never know, thanks again

---

### Post by Urmensch on 2008-07-21
I'm just curious why you are not using PHP's built in session functions for this? 

I've inherited code that uses this ill conceived cookie based login system and I have to say it seems worthless.

---


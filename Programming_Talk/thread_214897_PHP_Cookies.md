---
title: "PHP Cookies"
date: 2006-07-13
forum: Programming Talk
---

### Post by Ubuntuud on 2006-07-13
Hi,
I worked with javascript cookies first, what worked fine. But I'm having some problems with the PHP ones.

index.php
```
<?php
if (isset($_COOKIE["user"]))
{
	echo "<p>You are logged in.</p>";
}
else
{
	echo '<form action="http://hapake/includes/login.php" method="post">';
	echo 'Name: <input type="text" name="user" /><br />';
	echo 'Password: <input type="password" name="passwd" /><br /><br />';
	echo '<input type="reset" /><input type="submit" />';
	echo '</form>';
}
?>
```

login.php
```
<?php
setcookie("user", $_POST["user"], time()+31536000);
?>
```

When I fill in the form and submit it, login.php loads without errors. But when I load index.php again, it returns the else part, instead of the "you're logged in" part. Any ideas? Thanks in advance!

---

### Post by Ubuntuud on 2006-07-13
Hmmm... I noticed that the cookie does exist (screenshot). So the problem is the "isset" function. It isn't broken though, since it returns True when I put "isset($_POST["user"]" into "login.php"...

---

### Post by dabear on 2006-07-13
I have to ask, are you aware of what you are doing? 

You must not set one cookie with no required value to do this, what if I, from my browser, set the cookie my self? Then I would have complete access, and I'd bypass every validation steps you might have included, before you set the cookie.

Please also note that you should never ever use $_POST, $_GET etc directly, you must do validation, otherwise you willbe open to attacks such as mentioned above, cross site-scripting vulnerabilities and sql-attacks. Do a search at google for these various subjects.

about your problem, try to use !empty instead of isset. I would rather use another method for user validation, if you require users to be logged in; set the username and a sha1 hash of the password and a hash of the browsers last seen browser, and check if it's a match on next page load.

---

### Post by Ubuntuud on 2006-07-13
OK. Thanks. Right now I'm just toying around, but I can understand that it isn't very safe. I'll work on that. Thanks again!

EDIT: "!empty" doesn't work either...

---

### Post by MikeBenza on 2006-07-13
Aside from the fact, as mentioned above, you're violating some very basic security principles, the scripts work fine for me.  I suspect though that these scripts are just a simplified version of a problem on a large app.  

The cookie was set correctly (I checked using Live HTTP Headers on Firefox) and returned correctly in IE, Firefox, and Opera.  When I went back to index.php, I didn't have your problem: I got the logged in message.  Do you think you're getting the form because it's cached?

---

### Post by Ubuntuud on 2006-07-13
> **MikeBenza said:**
> Aside from the fact, as mentioned above, you're violating some very basic security principles, the scripts work fine for me.  I suspect though that these scripts are just a simplified version of a problem on a large app.  

The cookie was set correctly (I checked using Live HTTP Headers on Firefox) and returned correctly in IE, Firefox, and Opera.  When I went back to index.php, I didn't have your problem: I got the logged in message.  Do you think you're getting the form because it's cached?

I wasn't cached, since I cleared that with paranoia. But does it matter if it's an external file? "index.php" (the real name is "sidebar.php") is included in the real "index.php". Thank you for trying it out btw.

---

### Post by MikeBenza on 2006-07-13
I'm not sure what the problem might be.  Try this to dump all the variables:

[php]echo "<pre>" . print_R($GLOBALS, 1);[/php]

You should be able to find your user cookie and see what it's set to, then troubleshoot from there.

---

### Post by LordHunter317 on 2006-07-13
> **dabear said:**
> Please also note that you should never ever use $_POST, $_GET etc directly, you must do validation, otherwise you willbe open to attacks such as mentioned above, cross site-scripting vulnerabilities and sql-attacks. Do a search at google for these various subjects.Well, that's not quite true.  Proper DB drivers with parameterized query support can be thrown whatever input you want via a parameter and nothing bad will happen.

What is important is that one must consider all the avenues of input, and reliaze that any data provided by the user can potentially be spoofed by an attacker.

As such, we can't trust any sort of client identity (unless we're using client-side SSL certificates or things of that nature).  That means you never trust a user based on solely who they say they are: you force them to authorize.  You then put limitations on the authorization and don't send any data to the client that could potentially compromise the authorization tokens.

> set the username and a sha1 hash of the password and a hash of the browsers last seen browser, and check if it's a match on next page load.I would not send something like that at all.  Just generate some unique hashed data and send that, a GUID is sufficent.

---

### Post by Ubuntuud on 2006-07-13
```
[_COOKIE] => Array
        (
        )

    [HTTP_COOKIE_VARS] => Array
        (
        )


```

That's all I could find... Empty Arrays?

---

### Post by LordHunter317 on 2006-07-13
You have another issue with this code.  Likely, you're not setting the cookie early enough.  Unless output buffering is on, you must set a cookie before anything is rendered.

---

### Post by Ubuntuud on 2006-07-13
I'm sorry for the late response.
The login.php file consists of only one line, and that's the "setcookie" line. But it isn't on the index page. Does that matter? And I think I will indeed just cookie one line of hashed code, since it'll be for my dad's choir, and I'm planning on giving them only one username and password (maybe only a password).

---

### Post by Ubuntuud on 2006-07-14
I solved it! Not that it was hard... I guess it's impossible to put the "$_COOKIE" (and "$_POST" & "$_GET") reader on an external file and "require" it. So that's solved now. Thanks for your help.
But I have another question.
How can you protect the "secret pages" only available to people who have logged in? Thanks in advance!

---

### Post by Horsman on 2006-07-14
check for the cookie again!

---

### Post by Ubuntuud on 2006-07-14
Offcourse, stupid me. Thanks.

---

### Post by Horsman on 2006-07-14
> **Ubuntuud said:**
> Offcourse, stupid me. Thanks.

Don't be so hard on yourself. You're doing quite good.

For future problems, your first point of reference should probabally be the PHP manual. It has excellent documentation and lots of side tracks and helpful addendums. You'll be surprised with the amount of built in function.

---

### Post by Ubuntuud on 2006-07-16
OK. Thanks for the tip.

---


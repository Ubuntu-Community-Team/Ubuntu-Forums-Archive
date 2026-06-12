---
title: "php web redirect"
date: 2008-05-01
forum: Programming Talk
---

### Post by RadiationHazard on 2008-05-01
Ok, so I have a simple redirect already. I would really like it to ask for a username and password before it will redirect you though and if you get it wrong then i won't redirect you. Please if you know of one already made online or if you would be willing to make me one then that would be amazing!

-thank you!

---

### Post by mssever on 2008-05-01
> **RadiationHazard said:**
> Ok, so I have a simple redirect already. I would really like it to ask for a username and password before it will redirect you though and if you get it wrong then i won't redirect you. Please if you know of one already made online or if you would be willing to make me one then that would be amazing!

-thank you!

It shouldn't be too hard to write one yourself. Otherwise, you can use some pre-made CMS.

By the way, if all you have is a login followed by a redirect, how will you do anything with that on the destination page? In other words, how will you prevent somebody from going to that page directly without logging in?

---

### Post by RadiationHazard on 2008-05-01
> **mssever said:**
> It shouldn't be too hard to write one yourself. Otherwise, you can use some pre-made CMS.

By the way, if all you have is a login followed by a redirect, how will you do anything with that on the destination page? In other words, how will you prevent somebody from going to that page directly without logging in?

i only want to keep then out of that one page
and it only needs one username and pass

---

### Post by mssever on 2008-05-02
> **RadiationHazard said:**
> i only want to keep then out of that one page
and it only needs one username and pass

The easiest thing, then, would to use HTTP authentication. Apache has a several modules for that (mod_auth*).

---

### Post by Sportingfan on 2008-05-02
Hi,

as i understand, you just need a _post to a specified page.
Something like this:
```

<form method="post" action="secretPage.php">
Name:<input name="name" type="text"></input><br>
Password:<input name="password" type="password"></input><br>
<input type="submit" value="Submit">
</form>

```

And your secret page (named secretPage.php) looks like this:

```
<?php
	$name = addslashes($_POST["name"]);
	$password = addslashes($_POST["password"]);

	$user = "somename";
	$passw = "somepassw";
	if($name == $user && $password = $passw)
	{
		$body = "<b>you are a member</b>";
	}
	else
	{
		$body = "incorrect username and/or password";
	}
?>

<html>
<body>
<? echo $body; ?>
</body>
</html>
```

This is a very simple example! You should use a database containing the username and passwords.

I hope this is what you wanted to know.

---

### Post by xtal on 2008-05-02
If you are want to protect only one page its will be great to use Sportingfan's code.
If you want to redirect rather then posing the whole page you can choose between JS redirection (like this forum after you log in) or php redirection:

just send to the browser (before anything sent!):
[PHP]header('Location: http://www.example.com/');[/PHP]

or full code (stolen from Sportingfan):

```
<?php
	$name = addslashes($_POST["name"]);
	$password = addslashes($_POST["password"]);

	$user = "somename";
	$passw = "somepassw";
	if($name == $user && $password = $passw)
	{
		$body = "<b>you are a member</b>";
	}
	else
	{
                header('Location: http://www.mySite.com/Login.php');
	}
?>

<html>
<body>
<? echo $body; ?>
</body>
</html>
```

* I hope its working well

for more information please read this:
[http://il2.php.net/header](http://il2.php.net/header)

EDIT: u can write the whole page below because the user will leave ur page at the "header" line so he wont see the html code.

---

### Post by aamukahvi on 2008-05-02
> **xtal said:**
> If you are want to protect only one page its will be great to use Sportingfan's code.
If you want to redirect rather then posing the whole page you can choose between JS redirection (like this forum after you log in) or php redirection:

just send to the browser (before anything sent!):
[PHP]header('Location: http://www.example.com/');[/PHP]

or full code (stolen from Sportingfan):

```
<?php
	$name = addslashes($_POST["name"]);
	$password = addslashes($_POST["password"]);

	$user = "somename";
	$passw = "somepassw";
	if($name == $user && $password = $passw)
	{
		$body = "<b>you are a member</b>";
	}
	else
	{
                header('Location: http://www.mySite.com/Login.php');
	}
?>

<html>
<body>
<? echo $body; ?>
</body>
</html>
```

* I hope its working well

for more information please read this:
[http://il2.php.net/header](http://il2.php.net/header)

EDIT: u can write the whole page below because the user will leave ur page at the "header" line so he wont see the html code.

That's not entirely true. If the user agent has disabled redirects then the HTML would show. It's been a while since I did any PHP but I think you should do an exit() to end the execution of the current script.

---


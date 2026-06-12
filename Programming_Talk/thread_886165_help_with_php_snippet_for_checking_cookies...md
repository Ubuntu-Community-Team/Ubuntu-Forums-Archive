---
title: "help with php snippet for checking cookies.."
date: 2008-08-10
forum: Programming Talk
---

### Post by Mia_tech on 2008-08-10
I'm trying to come with some sort of php snippet to put on top of the members page after login and the code pretty much is checking for the existence of cookie... but for some reason is not working if someone could take a look at it
[PHP]<?php
//retrieving cookie and setting variable
$cookie = $_COOKIE['site_user'];

//checking for credentials..
if (isset($cookie)){
	if ( $cookie == md5("admin")) {
	    echo "welcome administrator";
	  }
  else {
	    echo "You are regular user";
	  }
else {
	header('Location: login.htm');
	}
}
?>[/PHP]

thanks

---

### Post by mssever on 2008-08-10
> **Mia_tech said:**
> but for some reason is not working if someone could take a look at it
Please define "not working." Also, it helps a lot if you indent your code properly. Your code is formatted in such a way that a quick glance makes it look like it's doing something different than it really is.

---

### Post by Mia_tech on 2008-08-11
well, if you don't understand it maybe you shouldn't reply ;0)

---

### Post by mssever on 2008-08-11
> **Mia_tech said:**
> well, if you don't understand it maybe you shouldn't reply ;0)
If you don't want me to reply, I won't. But I haven't seen anyone else replying.

The code you posted is OK (apart from the indentation issue). That's why I asked for more details. Saying it doesn't work is vague. Maybe the cookie isn't getting set in the first place. Maybe its something else. But you didn't provide enough information.

EDIT: One thing I did notice: $cookie will always be set when you test it. Perhaps you meant isset($_COOKIE['cookie_name']).

---

### Post by Mia_tech on 2008-08-11
yes the cookie is getting set as I'm using cookie editor in firefox and I'm looking at it....if I remove the isset($cookie) portion it works, what I mean is that it echoes "you're administrator" or "you're a regular user" depending on the cookie, but I want to be able to redirect any user trying to view the page that doesn't have the cookie set to the login page...hope this time I explain myself better


thanks

---

### Post by Mia_tech on 2008-08-11
thanks for the help I finally got it working..... with a little of moving code around
[PHP]<?php
//retrieving cookie and setting variable
$cookie = $_COOKIE['site_user'];

//checking for credentials..
if ($cookie == ""){
	header("Location: login.htm");
	}
	
if ( $cookie == md5("admin")) {
	    echo "welcome administrator";
	  }
  else {
	    echo "You are regular user";
	  }
?>[/PHP]

---

### Post by Reiger on 2008-08-11
And just on general principle you may want to avoid cookies for storing such sensitive information as "user rank".

Because... [http://gdataonline.com/seekhash.php](http://gdataonline.com/seekhash.php) there are reverse hash lookup tables out there... :D

---

### Post by Mia_tech on 2008-08-11
that's exactly what I'm trying to prove with my project... this is for a project by the way... I wouldn't use that in a live website, I will post the link to the final paper if someone would be interested, it's about related vulnerabilities with cookies and session impersonation/hijacking 


thanks

---


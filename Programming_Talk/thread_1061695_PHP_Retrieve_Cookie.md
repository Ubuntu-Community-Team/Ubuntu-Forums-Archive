---
title: "PHP Retrieve Cookie"
date: 2009-02-06
forum: Programming Talk
---

### Post by s.fox on 2009-02-06
Hi,

I have been getting really frustrated with a problem I have been experiencing with cookies and PHP.  Basically I have set a cookie but in certain web browsers I can't seem to retrieve it.  This is proving very confusing, as i would think that the same piece of php code work the same way in all web browsers.   

Specifcally I am having trouble with camino and some versions of firefox.

```

<?php
$cookieValue = $_COOKIE['cookieName'];
echo $cookieValue;
?>

```

The cookie is definately set, so that makes me think its not anything to do with security.   If anyone could help me out on this one I would be very grateful.

Many Thanks,
-Ash R

---

### Post by Reiger on 2009-02-06
Does 'certain webbrowsers' _accept_ Cookies by default (or from your site for that matter)?

---

### Post by s.fox on 2009-02-06
Hi,

Yes, the cookies must be accepted otherwise i would not be able to create the cookie in the first place.   Its still puzzling,   

-Ash R

---

### Post by s.fox on 2009-02-07
Hi,

I got it sorted.  It looks like it was something to do with the way my scripts were navigating around my site using header redirects.  I solved it by redirecting to a "middle man script" that instantly redirects again to the main script which needs to access the cookie.  Kinda puzzling why going directly to the script which would retrieve the cookie did not work.  Anyway,  its sorted now and that's the main thing.   Of course any input on why I was this problem would be fantastic.

-Ash R

---

### Post by s.fox on 2009-02-10
Hi again,

Looks like I was wrong.  The problem is not solved.  Here is the process flow for my scripts:

1) Script#1 creates cookie and then redirects to my main page
2) From main page a user clicks a regular HTML Link to another page (Script#2)
3) Script#2 should retrieve the cookie that was set earlier.

Does anyone has any idea why i the cookie is not being retrieved correctly?

Many thanks,

-Ash R

---

### Post by tturrisi on 2009-02-10
Put this on page 2.

```
$cookieValue = $HTTP_COOKIE_VARS["name-of-the-cookie"];
```

For example, if set a cookie like so:
```
$user_id = "John Doe";
setcookie("valid_user",$user_id);
```
then retrieve & display the user_id like this:
```
$cookieValue = $HTTP_COOKIE_VARS["valid_user"];
echo $cookieValue;
```

[http://us3.php.net/setcookie](http://us3.php.net/setcookie)

Note: a browser is limited to 20 cookies/domain, thus it's a good idea to cleanup (delete) the unneeded cookies when the session ends, or at least put a time limit value in the cookie.

---

### Post by s.fox on 2009-02-15
Hi,

Unfortunatly that didn't work.  I am starting to think it may not be anything to do with retreiving the cookie.  I think it may be something to do with how the cookie was set in the first place,  more specifically the domain.  This is how my script sets the cookie I want to retrieve.


```

$future = 60 * 60 * 24 * 1 + time();  
setcookie("cookieName", "$cookieData", $future);

```I did a little research on php.net and found this example.

```

[COLOR=#000000][COLOR=#0000bb]setcookie[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"TestCookie"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$value[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]time[/COLOR][COLOR=#007700]()+[/COLOR][COLOR=#0000bb]3600[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"/~rasmus/"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]".example.com"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]1[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700][COLOR=Black]
Can someone please clarify what the "/~rasmus/" is all about?  Is it the path?  If so should i use "/" to make it available on all of my sites directories?  If I just had the .example.com part would this do exactly the same thing?  

Sorry for all the questions,  but this is something that has confussed me a little.

Many thanks,

-Ash R[/COLOR]
[/COLOR][/COLOR]

---

### Post by Reiger on 2009-02-15
It's explained in the parameter list, here: [http://nl.php.net/setcookie](http://nl.php.net/setcookie)

EDIT: "/~rasmus/" is the path of pages for which the client should send the cookie when visiting $domain.
So if you have a directory tree under the $domain like this:
```

$domain/foo/index.php
$domain/foo/baz/page.php
$domain/bar/index.php

```

Then a cookie with $path = "/foo/" will not be sent to $domain/bar/index.php, but will be available to $domain/foo/index.php and $domain/foo/baz/page.php.

---

### Post by tturrisi on 2009-02-15
> **Ash R said:**
> Hi,

Unfortunatly that didn't work.  I am starting to think it may not be anything to do with retreiving the cookie.  I think it may be something to do with how the cookie was set in the first place,  more specifically the domain.  This is how my script sets the cookie I want to retrieve.


```

$future = 60 * 60 * 24 * 1 + time();  
setcookie("cookieName", "$cookieData", $future);

```I did a little research on php.net and found this example.

```

[COLOR=#000000][COLOR=#0000bb]setcookie[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"TestCookie"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$value[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]time[/COLOR][COLOR=#007700]()+[/COLOR][COLOR=#0000bb]3600[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"/~rasmus/"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]".example.com"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]1[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700][COLOR=Black]
Can someone please clarify what the "/~rasmus/" is all about?  Is it the path?  If so should i use "/" to make it available on all of my sites directories?  If I just had the .example.com part would this do exactly the same thing?  

Sorry for all the questions,  but this is something that has confussed me a little.

Many thanks,

-Ash R[/COLOR]
[/COLOR][/COLOR]
Why on earth do you nead the var $future?
Why not just standardly set the cookie:
```
setcookie("name", "value", time()+3600*24);
```

---

### Post by s.fox on 2009-02-20
Hi,  sorry for not getting back on this topic.  I have just been swamped by others things.

Looks like I was right when I thought it could be something to do with the domain of the cookie.  Slightly annoyed that web examples I saw of setting the cookie in PHP didn't use that argument, but still I have learnt something.   I think in future I shall use all the arguments in any function just to play it safe.

Once again, many thanks 

-Ash R

P.S @tturrisi- I had the expirary timne in a variable so I could reuse it later in the script if I wanted to.  No other real reason.  Thanks for the comments though

---

### Post by tturrisi on 2009-02-22
...

---

### Post by tturrisi on 2009-02-22
> **Ash R said:**
> 
P.S @tturrisi- I had the expirary timne in a variable so I could reuse it later in the script if I wanted to.  No other real reason.  Thanks for the comments though

What I do when I need the expiry time is grab the cookie values on each page as I need them.  For example, I ahve a site where the user is allowed indefinite sesion length but gets auto logged out after 15 minute innactivity.  I use javascript & php to do that.  In this case I store the login time in a database table and pull it as needed.  This is more secure than using the time value in a cookie as the user can modify his cookie values.  All I store in the cookie is the user_id.

I set a cookie at login:
```
$sql = "SELECT user_id,userpass FROM logins WHERE user_id='$user_id' AND userpass='$userpass'";
$result = mysql_query($sql);
mysql_close();
	
	if (mysql_num_rows($result) != 1)
	{
	header("location: login.php");
	exit;
	}
	else {
	 //if user_id and userpass ok
	session_start();
	setcookie("valid_user",$user_id);	
	include ("./inc/dbconnect.php");
	$login_time = time();
	$sql = "UPDATE logins SET login_time='$login_time' WHERE user_id='$user_id'";
	$result = mysql_query($sql);
	mysql_close();
	header("location: users/");
	exit;
	}
```

On each page I validate the user:
```
// get user_id stored in the cookie
$user_id = $HTTP_COOKIE_VARS["valid_user"];
include ("dbconnect.php");
$sql = "SELECT * FROM logins WHERE user_id='$user_id' AND is_approved='yes'";
$result = mysql_query($sql);
$myrow = mysql_fetch_array($result);
$login_time = $myrow["login_time"];

	// if not logged in kick out user
	if (mysql_num_rows($result) != 1) {
	mysql_close();
	header("location: ../login.php");
	exit;
	}
	
$now = time();
$time_diff = $now - $login_time;

	if ($time_diff >= 900){
	mysql_close();
	session_destroy();
	header("location: ../login.php");
	exit;
	}
	
	else {
	$login_time = time();
	$sql = "UPDATE logins SET login_time='$login_time' WHERE user_id='$user_id'";
	$result = mysql_query($sql);
	mysql_close();
	}
?>
```

I display the "time left" in red on the page using a javascript countdown:

```
// $login_time var is a result from vaild user check
// add 15 minutes to login_time
$max_time = $login_time + "900";
$now = time();
$seconds_left = $max_time - $now;

// Convert $seconds_left to minutes and seconds
$minutes = intval(($seconds_left / 60) % 60);
$minutes = str_pad($minutes, 2, "0", STR_PAD_LEFT);
$seconds = intval($seconds_left % 60);
$seconds = str_pad($seconds, 2, "0", STR_PAD_LEFT);
?>
<script type="text/javascript">
var minutes = <?php echo $minutes; ?>;
var seconds = <?php echo $seconds; ?>;
function countdown(){
	if(minutes >= 0 && seconds >= 0){
		var mins = (minutes < 10 ? "0" : "") + minutes;
		var secs = (seconds < 10 ? "0" : "") + seconds;
		document.getElementById("time_left").innerHTML = mins + ":" + secs;
		if(seconds == 0){
		minutes = minutes -1;
		seconds = 59;
		}
		else {
		minutes = minutes;
		seconds = seconds - 1;
		}
	}
	if(minutes == 0 && seconds == 0){
	alert("Your session has expired!\nLogin again to continue.")
	window.location="../logout.php";
	}
setTimeout("countdown()", 1000);
} //end function
</script>
```

Call the javascript at page load:

```
<body onload="countdown()">
```

Display the "time left" on the page (clock that counts backwards from 15:00):

```
<p>Time Left: <span id="time_left" class="red"></span></p>
```

---


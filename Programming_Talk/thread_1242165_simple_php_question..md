---
title: "simple php question."
date: 2009-08-16
forum: Programming Talk
---

### Post by hockey97 on 2009-08-16
Hi, I want to know how in php can I delay certain part of the script from running?

For example lets say I have an area where you need to be logged in. I want the user to click on a link which will run a php script which will figure out if they are logged in or not and if they are not logged in I want to display a text saying sorry you need to login for at least 30 secs. Then I want to redirect the user to the login page.

How do you make that delay? I thought of using sleep() function but when I used it. It would then do a 30sec delay in running the script at all. You see the page having a loading wait from the browser for 30secs then you see the text for like 1 or 2 seconds and then redirects the user to the login screen. 

I want them to be able to read the message before they get redirected. What do I need to do? do I use sleep or another functions or do I create a count down timer?

---

### Post by Can+~ on 2009-08-16
You could do it with javascript.

[http://www.w3schools.com/js/js_timing.asp](http://www.w3schools.com/js/js_timing.asp)

---

### Post by twright on 2009-08-16
Yes, Javascript is the best way to do this as sleep in php just pauses the generation of the page/running of the script.

Generally you should use php when doing stuff with data on the server i.e processing a form, processing user logins or displaying variable text and stick to javascript/html for the actual static webpage bits.

---

### Post by hockey97 on 2009-08-16
Updated: I got it to work forgot one ". Thanks it works now.

---

### Post by Can+~ on 2009-08-16
> **hockey97 said:**
> I just gave that javascript a try. I still get the same results with php sleep.

I would see the text split of a second and then the user gets redirected.

I have this code under a if else statement. 

so far I don't see anything that shows any slow down of the code after the message you have to login.

For starters, don't use sleep any more on a server for this (other situations may call it).

Second, use javascript and, for example, add a first timeout event that will throw the message (dunno how you want to do this, a nice way would be to put the page with a black transparent layer like when opening a gallery) and then a second to redirect him.

---

### Post by Can+~ on 2009-08-16
Here's a working example

[HTML]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
   <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
   <meta name="keywords" content="HTML, tags, commands">
   <title>Index</title>
	
	<script language="javascript" type="text/javascript">
	// <!-- Old stuff is old
	
	function timeout_redirect()
	{
		document.getElementById("txt").value="Consider yourself redirected.";
	}
	
	function timeout_alertuser()
	{
		document.getElementById("txt").value="You'll be redirected in 3s.";
		
		var t=setTimeout("timeout_redirect()", 3000);
	}
	
	function timeout_init()
	{
		document.getElementById("txt").value="You'll be alerted in 3s.";
		
		var t=setTimeout("timeout_alertuser()", 3000);
	}
	
	// -->
	</script>
	
	<!--<link href="css/style.css" rel="stylesheet" type="text/css">-->
</head>
<body>

This is my website, there are many like'em, but this one is mine.
<form>
<input type="button" onclick="timeout_init()" id="btninit" value="Start counting!" width="20" />
<input type="text" id="txt" />
</form>

</body>[/HTML]

---


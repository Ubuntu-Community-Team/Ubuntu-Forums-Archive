---
title: "PHP &quot;elseif&quot; help"
date: 2009-05-25
forum: Programming Talk
---

### Post by dhtseany on 2009-05-25
Hi all,
I'm having problems using an "elseif" statement. If someone could have a look and see what I'm doing wrong that'd be great :)

Thanks in advance,
Sean

PS- Sorry if this is considered double posting, but I thought that these were two seperate issues. If you check out my other post you'll at least see what I'm trying to use this for. ;)
[http://ubuntuforums.org/showthread.php?t=1169019](http://ubuntuforums.org/showthread.php?t=1169019)
```

<?
session_start();
if (!isset($_SESSION['username'])) {
echo "<meta http-equiv='refresh' content='0;URL=login.php' />";
echo "Please log in...";
exit;}
elseif (!isset($_SESSION['priv']) 
	|| $_SESSION['priv'] !== '1') {
echo "You are not authorized to view this page. Please wait.";
echo "<meta http-equiv='refresh' content='2;URL=members.php' />";
} else {
echo "
It's working";}
endif;
?>

```

---

### Post by Zimmer on 2009-05-25
> **dhtseany said:**
> Hi all,

<?
session_start();
if (!isset($_SESSION['username'])) {
echo "<meta http-equiv='refresh' content='0;URL=login.php' />";
echo "Please log in...";
exit;}
elseif (!isset($_SESSION['priv']) 
	|| $_SESSION['priv'] !== '1') {
echo "You are not authorized to view this page. Please wait.";
echo "<meta http-equiv='refresh' content='2;URL=members.php' />";
} 
****** an endif required here????

else {
echo "
It's working";}
endif;
?>
[/code]




Not a PHP programmer, but I think you need the elseif terminated... as shown ?
NOPe, wrong there on consulting the manual :)

Perhaps you should check whether your conditions are being met by the statements and your logic is sound.

---

### Post by dhtseany on 2009-05-25
Thanks for the response.

I figured an "endif;" was needed, but I've never tried putting 2 IFs together. As you suggested, I tried putting an endif; in a few different places but none of them work. I keep getting:
```

Parse error: syntax error, unexpected T_ENDIF in /../public_html/secure/admin.php on line 12

```

Any other suggestions?

---

### Post by Zimmer on 2009-05-25
I was wrong there, see above...
but $_SESSION['username']

not sure I see the reason for the quotes, would that not resolve as plain text username and not the contents of the variable username?

---

### Post by wieman01 on 2009-05-25
Could you just verbally try to explain what you are trying to do with the different if-statements / sections?

---

### Post by Zimmer on 2009-05-25
[http://www.free2code.net/tutorials/view/php_sessions-11/page1.html](http://www.free2code.net/tutorials/view/php_sessions-11/page1.html)

This any help?

---

### Post by dhtseany on 2009-05-25
OK, here is what I'm trying to do:

I've setup a working user authentication "system" using PHP and MySQL for username and password storage. What I'm trying to do now is setup user levels (admin vs. end user). To accomplish this I added an additional field into the SQL table where UN/PW's are stored. (1 in the "priv" field will mean admin and 2 will mean end user). So far I've setup the login page to create a separate session ($_SESSION['priv'];) to check against and I've setup a simple check to determine that the priv session was successfully created, so I know the login parts are working.

What I'm trying to do now is get this piece of code working that will go on all "admin_blahblahblah.php" pages to not only verify that the user is logged in with an active session ($_SESSION['username'];) but also verify that their priv session is showing "1", indicating that they are an admin.

Make sense? ;)

---

### Post by dhtseany on 2009-05-25
> **Zimmer said:**
> [http://www.free2code.net/tutorials/view/php_sessions-11/page1.html](http://www.free2code.net/tutorials/view/php_sessions-11/page1.html)

This any help?

Sorry, but I already understand how to *use* sessions. What my problem is combining multiple IF statements so on certain restricted pages the 2 sessions I have active are checked against.

Thank you, though.

---

### Post by wieman01 on 2009-05-25
Try this instead... your code contained a few errors. Is that what you want?
```
<?

session_start();

if (!isset($_SESSION['username'])) {

	echo "<meta http-equiv='refresh' content='0;URL=login.php' />";
	echo "Please log in...";
} elseif (!isset($_SESSION['priv']) OR $_SESSION['priv'] != '1') {

	echo "You are not authorized to view this page. Please wait.";
	echo "<meta http-equiv=refresh content=2;URL=members.php />";
} else {

	echo "It's working";
}

?>
```
Another question... Did you program the login function yourself? Have you heard of SQL injections?

---

### Post by Zimmer on 2009-05-25
Thanks guys!
just spent an interesting hour at php.net  :)

---

### Post by dhtseany on 2009-05-25
> 
Is that what you want?

Yes :) However, could you explain to me what I did wrong? I'm trying to learn without relying on other people to fix my errors for me. I see that you added an OR statement. Was that my screwup?

> 
Did you program the login function yourself? Have you heard of SQL injections?

Yes, I programmed it myself. I'm aware of SQL injections, but I've never really worried about it until now. Do you have any "simple" explanation articles that I can read?

> 
Thanks guys!
just spent an interesting hour at php.net


Haha, no problem. I was reading up over there but I was having a hard time finding the info I needed. (Over the years I've been to php.net many times and I just never liked their explanations of how this stuff works ;))

Thanks for your help though!

---

### Post by wieman01 on 2009-05-25
There were a number of things that needed correcting... Let me summarize:

**A. $_SESSION['priv'] !== '1'**

It's != in fact.

**B. echo "<meta http-equiv='refresh' content='0;URL=login.php' />";**

It's always tricky to have ' between " or vice versa.

**C. endif;**

You don't need that.
[B]
D. AND vs. OR[/B]

Think about it... you want to check the session property "priv" is set and equals "1". If the property does not match either of those criteria, access is denied. Does that make sense (it's late here...)?

This is an interesting read on SQL injections:

[http://de.wikipedia.org/wiki/SQL-Injection]("http://de.wikipedia.org/wiki/SQL-Injection")

Please read it carefully because SQL injections are a serious threat. With a single line of code (disguised as username for instance) an malicious hacker can delete your entire database. Just like that. Tested it before.

Keep up the good work! :-)

---

### Post by dhtseany on 2009-05-25
Thanks for all the help! 
I see what you mean now with the errors. I'll be sure to read up on the SQL Injections.

Peace
Sean

---


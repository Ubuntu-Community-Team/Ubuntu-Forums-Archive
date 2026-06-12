---
title: "PHP Error &quot;Missing semicolon&quot;"
date: 2009-12-19
forum: Programming Talk
---

### Post by dmillerw on 2009-12-19
```
<?php
$PWord = ?> <SCRIPT LANGUAGE="Javascript">
var lastname = "<?php echo $_POST['LName']; ?>";
lastname = lastname.toLowerCase();
var ssid = "<?php echo $_POST['StuID']; ?>";
var password = lastname.substring(0,2) + ssid.substring(2);
</SCRIPT>
<?php
```

Thats the code thats giving me the error, I'm attempting to have that run and output the php var password as $PWord

If I run that code the way it is...

> 
Parse error: syntax error, unexpected ';' in /opt/lampp/htdocs/database/insert.php on line 2

...I get that

Any help would be appreciated

I know that there's something wrong with the syntax, just can't figure out how to fix it

---

### Post by Arndt on 2009-12-19
> **dmillerw said:**
> ```
<?php
$PWord = ?> <SCRIPT LANGUAGE="Javascript">
var lastname = "<?php echo $_POST['LName']; ?>";
lastname = lastname.toLowerCase();
var ssid = "<?php echo $_POST['StuID']; ?>";
var password = lastname.substring(0,2) + ssid.substring(2);
</SCRIPT>
<?php
```

Thats the code thats giving me the error, I'm attempting to have that run and output the php var password as $PWord

If I run that code the way it is...



...I get that

Any help would be appreciated

I know that there's something wrong with the syntax, just can't figure out how to fix it

The error message says "unexpected semicolon", but you are probably right in assuming that one is missing, or some other syntax error.

If you remove the first part, <?php $PWord = ?>, php can process your file. The first part isn't a complete PHP statement, so what is it meant to do?

---

### Post by kwyto on 2009-12-19
i don't know PHP, but i'm looking at a tutorial and i see a difference with your code:
<?php echo $_POST['LName']; ?>
 
here is the code from the tutorial:
Welcome <?php echo $_REQUEST["fname"]; ?>!<br />
You are <?php echo $_REQUEST["age"]; ?> years old.

you are using single quotes and the tutorial uses double quotes for the variables. "fname"   'LName'

---

### Post by Arndt on 2009-12-19
> **kwyto said:**
> i don't know PHP, but i'm looking at a tutorial and i see a difference with your code:
<?php echo $_POST['LName']; ?>
 
here is the code from the tutorial:
Welcome <?php echo $_REQUEST["fname"]; ?>!<br />
You are <?php echo $_REQUEST["age"]; ?> years old.

you are using single quotes and the tutorial uses double quotes for the variables. "fname"   'LName'

That is not an error. Double and single quotes can both surround a string. There is a difference if the string includes a variable, then double quotes must be used. Similar to shell syntax.

---

### Post by kwyto on 2009-12-19
ok, i see, then dmillerw should say if LName is either a string or a variable. most of the times its an stupid mistake, but you looking so desperately to find that you can't see it in from of your eyes. just take a break and come back at it later with a fresher mind and eyes.

---

### Post by Hellkeepa on 2009-12-19
HELLo!

First just let me make a quick note about single-quoted vs double-quoted strings: Double-quoted strings are more feature-richs than single-quoted, not only in being able to use variables within the defined string. Please have a look in the [PHP manual](http://no2.php.net/manual/en/language.types.string.php) for all of the details on this.

Secondly, the code:
As previously mentioned, your error lies in the first line, that it is incomplete. I also notice that you haven't quite understood how PHP works, in the server-client model. Something which is quite common for beginners. Anyway, what you need to know is that PHP is processed on the server, before the HTML content is sent to the browser. In other words, the PHP and HTML code is seperate, and as such PHP does not know about anything that's not between the PHP-tags.
That is why I recommend doing *all* of the PHP code at the top of the document, before writing any HTML. Using variables to output the generated content into the HTML-code, at their desired locations. This won't just help you keep in control of the code, and as such make it easier to understand and mantain, but it'll also make sure you got the full capabilities of PHP at all times. Certain functions, like session, cookie and header functions need to be used before any HTML is sent to the browser.

Thirdly, security:
Since you do not escape the output using "htmlspecialchars()", anyone can alter your HTML code. They can even inject JavaScript, which can be used for a multitude of attacks. I recommend that you research "input validation" and "output escaping", to learn how to write secure applications. Knowledge usable in any programming language. ;-)
I'd also choose a completely random password, and adding a salt to it before hashing it. Using the above method means that all that anyone needs to know to "crack" the password of anyone, is their last name and student ID. Not exactly private information, I'd imagine.

Fourthly, the fix:
From what I was able to glean from your code, you want the password to be set to the first two characters of the lastname, plus the stud ID number minus the two first characters. There is two main issues with your code for this.
[list=1][*]JavaScript is executed on the client only, while PHP is on the server. Meaning these two can only "communicate" one way, namely from PHP to JS (by constructing the JS via PHP's "echo").
[*]"$PWord = ?> " <- Tells PHP to set PWord to nothing, or not actually "nothing", but something undefined. Something which will cause strange parsing issues.[/list]
So what PHP actually sees, is this:
```
<?php
$PWord = ;
echo $_POST['LName'];
echo $_POST['StuID'];
?>
```

I've written up a quick example of how I'd do it, or at least roughly how I'd do it. You'll find it here: [http://pastebin.com/f7f1c4958](http://pastebin.com/f7f1c4958)
Notice that I've removed the JS entierly, no need to have it there as everything is computed on the server.

Happy codin'!

---

### Post by dmillerw on 2009-12-19
EDIT: Didn't notice the reply above

---

### Post by dmillerw on 2009-12-19
> **Hellkeepa said:**
> HELLo!

First just let me make a quick note about single-quoted vs double-quoted strings: Double-quoted strings are more feature-richs than single-quoted, not only in being able to use variables within the defined string. Please have a look in the [PHP manual](http://no2.php.net/manual/en/language.types.string.php) for all of the details on this.

Secondly, the code:
As previously mentioned, your error lies in the first line, that it is incomplete. I also notice that you haven't quite understood how PHP works, in the server-client model. Something which is quite common for beginners. Anyway, what you need to know is that PHP is processed on the server, before the HTML content is sent to the browser. In other words, the PHP and HTML code is seperate, and as such PHP does not know about anything that's not between the PHP-tags.
That is why I recommend doing *all* of the PHP code at the top of the document, before writing any HTML. Using variables to output the generated content into the HTML-code, at their desired locations. This won't just help you keep in control of the code, and as such make it easier to understand and mantain, but it'll also make sure you got the full capabilities of PHP at all times. Certain functions, like session, cookie and header functions need to be used before any HTML is sent to the browser.

Thirdly, security:
Since you do not escape the output using "htmlspecialchars()", anyone can alter your HTML code. They can even inject JavaScript, which can be used for a multitude of attacks. I recommend that you research "input validation" and "output escaping", to learn how to write secure applications. Knowledge usable in any programming language. ;-)
I'd also choose a completely random password, and adding a salt to it before hashing it. Using the above method means that all that anyone needs to know to "crack" the password of anyone, is their last name and student ID. Not exactly private information, I'd imagine.

Fourthly, the fix:
From what I was able to glean from your code, you want the password to be set to the first two characters of the lastname, plus the stud ID number minus the two first characters. There is two main issues with your code for this.
[list=1][*]JavaScript is executed on the client only, while PHP is on the server. Meaning these two can only "communicate" one way, namely from PHP to JS (by constructing the JS via PHP's "echo").
[*]"$PWord = ?> " <- Tells PHP to set PWord to nothing, or not actually "nothing", but something undefined. Something which will cause strange parsing issues.[/list]
So what PHP actually sees, is this:
```
<?php
$PWord = ;
echo $_POST['LName'];
echo $_POST['StuID'];
?>
```

I've written up a quick example of how I'd do it, or at least roughly how I'd do it. You'll find it here: [http://pastebin.com/f7f1c4958](http://pastebin.com/f7f1c4958)
Notice that I've removed the JS entierly, no need to have it there as everything is computed on the server.

Happy codin'!

Alright, I took a look at your code, all I really needed however was the one line 

```
$Password = substr ($_POST['LName'], 0, 2).substr ($_POST['StuID'], 2);
```

I do appreciate the help however.

Thanks a bunch!

One question however, how would I strip all capitalization from LName

---

### Post by Hellkeepa on 2009-12-20
HELLo!

I recommend you read a bit up in the [PHP-manual](http://www.php.net/manual/en/), especially the sections "Language Reference", "Security", "Features", and the "Text Processing" and "Variable and Type Related Extensions" subsections of the "Function reference".
There you'll find a lot of necessary information for you to build solid applications, and use PHP to its full extent. You'll find what you're looking for in the "Text processing" subsection, naturally enough. ;-)

PS: Making the password all lower-case lessens the security even more, to the point where having a password is pointless.

Happy codin'!

---

### Post by dmillerw on 2009-12-20
Thanks for the link.

Security at the moment is not a big issue for me, as its limited to my home network, and is just for me testing things.

---

### Post by Hellkeepa on 2009-12-21
HELLo!

You're welcome.
As for security, while you may not need it at this point of time, the best time to learn it is from the word go. That way, you don't need to change bad habits later on, or go back and change stuff you've done, but get a clean and secure design at once. ;-)

Happy codin'!

---


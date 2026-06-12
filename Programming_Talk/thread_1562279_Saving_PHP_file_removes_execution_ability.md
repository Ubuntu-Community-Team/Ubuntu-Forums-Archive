---
title: "Saving PHP file removes execution ability"
date: 2010-08-27
forum: Programming Talk
---

### Post by MaindotC on 2010-08-27
I'm learning PHP and trying to do some exercises from the book.  Summarizing - when I save the php file with HTML in it, the php appears to lose execution abilities.

Long explanation:  I created a form called generic_form.html that calls display_input.php.  When I add the html to display_input.php, gedit will remove the colouring from the php code.  Here are the contents:

```
<HTML>
<HEAD>
<TITLE>Generic Input Form</TITLE>

</HEAD>
<BODY>

<form method = "post" action = "display_input.php">
<p><strong>Text Field:</strong><br>
<textarea name = "text1" cols = 45 rows = 5 wrap = virtual></textarea></p>

<p><strong>String Function:</strong><br>
<input type = "radio" name = "func" value = "md5"> get md5<br>
<input type = "radio" name = "func" value = "strlen"> get length of string<br>
<input type = "radio" name = "func" value = "strrev"> reverse the string<br>
<input type = "radio" name = "func" value = "strtoupper"> make string uppercase<br>
<input type = "radio" name = "func" value = "strtolower"> make string lowercase<br>
<input type = "radio" name = "func" value = "ucwords"> make first letter of all words uppercase</p>

<p><input type = "submit" name = "submit" value = "Do something with the string"></p>

</form>
</BODY>
</HTML>

```

And here's display_input.php per what the book instructs me to type:
```
<? if (($_post[text1] == "") || ($_post[func] == "")) {
	header("Location: generic_form.html");
	exit;
}

$result = $_post[func]($_post[text1]);

?>

<HTML>
<HEAD>
<TITLE>Generic Input Results</TITLE>
</HEAD>
<BODY>

<? echo "$result"; ?>
<p><a href = "generic_form.html">Go again!</a></p>

</BODY>
</HTML>

```

When I try executing the form, there is an error generated in apache:```

[Fri Aug 27 11:02:33 2010] [error] [client 127.0.0.1] script '/var/www/display_input.php' not found or unable to stat, referer: http://localhost/test.php
```

Here's what it looks like when I remove the html section (sorry about the overlay - forgot to turn off desktop effects): [IMG]http://a.imageshack.us/img189/4530/69605083.png[/IMG]

And when I leave the html in it:[IMG]http://a.imageshack.us/img838/1467/72084015.png[/IMG]

Why is this happening?  Thanks!

---

### Post by C00re on 2010-08-27
This is wrong: **<?** echo "foo"; **?>**
This is correct: **<?php** echo "foo"; **?>**

---

### Post by v8YKxgHe on 2010-08-27
removed

---

### Post by MaindotC on 2010-08-27
> **C00re said:**
> This is wrong: **<?** echo "foo"; **?>**
This is correct: **<?php** echo "foo"; **?>**

Thank you for the reply!  For some reason I didn't have to define that before - I could simply use <?.  I replaced it as you advised and the file now saves correctly.

Alex - you are right and in fact the person that gave it to me told me it was a crap book, but I just thought I'd give it a try.  I'm not sure if it gets into security considerations but I'll use the link you suggested or even w3schools.

Thank you both for replying.  Surprisingly much better help than I got in ##php...

---


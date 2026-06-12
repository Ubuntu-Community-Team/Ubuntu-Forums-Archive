---
title: "Defining php constant to prevent direct access...error!"
date: 2008-12-18
forum: Programming Talk
---

### Post by lucas4ce on 2008-12-18
In an attempt to prevent direct access to my scripts and included files I have defined constants using the define() function, which are then checked in the script files, and I have used the die() function if the constant is not defined.

This does work, i.e. I cannot access the scripts and included files directly by typing in their url path, and I receive the die("text here") message.

However when running the webpage normally I am getting a "; expected" error in both IE and Firefox.  In Firefox the debugger error states:

missing ; before statement text here.

I have narrowed down the problem to a costant definition in the <head> section of the main webpage, so for example I've done this:

[HTML]<head>
  	<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
	<meta http-equiv="Content-type" content="text/html; charset=utf-8" />
  	<title>Title</title>
	<link rel="stylesheet" href="mypage.css" type="text/css" />
	[PHP]<?php define("AUTHR",1); ?>[/PHP]
	<script src="myscripts.php" type="text/javascript"></script>
</head>[/HTML]

..so that the constant AUTHR is defined before the script is called, allowing the page to open properly.

I'm guessing I can't do this, or if I can I've gone about it the wrong way.

Any ideas or solutions would be very gratefully received!!

---

### Post by mssever on 2008-12-18
> **lucas4ce said:**
> However when running the webpage normally I am getting a "; expected" error in both IE and Firefox.  In Firefox the debugger error states:

missing ; before statement text here.

I have narrowed down the problem to a costant definition in the <head> section of the main webpage, so for example I've done this:

[html]<head>
      <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
      <title>Title</title>
    <link rel="stylesheet" href="mypage.css" type="text/css" />
    [php]<?php define("AUTHR",1); ?>[/php]
    <script src="myscripts.php" type="text/javascript"></script>
</head>[/html]..so that the constant AUTHR is defined before the script is called, allowing the page to open properly.
Are you saying that the exact code you posted doesn't work when it's the only code in the entire file? While your code has some oddities (is the charset ISO-8859-1 or UTF-8? What's with the [noparse][php] and [/php][/noparse]?), your PHP is correct. Your bug must be somewhere else.

---

### Post by lucas4ce on 2008-12-18
mssever,

Thank you for your reply.

They are php flags inserted by this forum, I wont do that next time.

The charset is UTF-8 I think, everything seems to work with either, can't quite remember why there were both charsets in that <head> section.  I've changed that to just show one now and it didn't solve the bug.

The code I posted is just the <head> section of the webpage.  I have a similar constant definition in the <body> section just before an included php file, and this works fine.

If I remove the constant definition from the <head> section, and the corresponding definition check in the script file, everything works.  But of course I can directly access the script file.

Thanks, I'll keep looking.

---

### Post by Izek on 2008-12-18
How is this...
```
<script src="myscripts.php" type="text/javascript"></script>

```
even possible?

HTML Files can't even use PHP to begin with. Or is the code given in a **.php** file?

```
<?php include "myscripts.php"; ?>
```

---

### Post by lucas4ce on 2008-12-18
Hi Izek,

Thanks for your reply.

Yes that does stop the "; expected" error, but then my scripts and functions are pasted at the top of my webpage output.

I'm using the <script src="" /> so that the webpage uses the functions in the script file, rather than outputting them.

The webpage is a php file not an html file.

---

### Post by Reiger on 2008-12-18
> **Izek said:**
> How is this...
```
<script src="myscripts.php" type="text/javascript"></script>

```
even possible?


Remember: src points to a resource, not to a file. That's a subtle difference, but it is this behaviour which makes it possible for PHP to generate directly used images, CSS, JavaScript etc. The OP presumably wants his PHP file to generate the JavaScript dynamically.

> 

HTML Files can't even use PHP to begin with. Or is the code given in a **.php** file?
That, or the JavaScript is dynamically generated and streamed as if it were a file (see remark above).

> 

```
<?php include "myscripts.php"; ?>
```

Which would (likely) not validate (if that were a concern) and may not work due to the invalid characters '&' and '<'.

Also I would not use:
<script src="my_resource" type="text/javascript" /> because browsers such as MSIE don't like empty script tags very much. At least it never did when I tried to offer it these empty tags. (Curse you MSIE, for forcing me to include bogus comments in the output of my XSLT...!)

---

### Post by michaelzap on 2008-12-18
You may need to set the content type in myscripts.php so that the browser will treat it as a javascript file:
```
<?php
header("Content-type: text/javascript");
... (the rest of your script)
?>
```
Headers must be set before ANY output is sent to the document (including spaces outside of the php tags).

---

### Post by Izek on 2008-12-18
>>Delete Post<<

---


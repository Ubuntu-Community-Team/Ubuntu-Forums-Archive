---
title: "php $_POST"
date: 2007-02-03
forum: Programming Talk
---

### Post by Ubuntuud on 2007-02-03
Hi,

I need to 'pass' a ($_POST) variable.

So when I have this form:
[HTML]<form action="processor.php">
<input type="hidden" name="info" value="info" />
<input type="submit" name="one" value="one" />
<input type="submit" name="two" value="two" />
</form>[/HTML]
I want this page (processor.php):
[HTML]if ($_POST['one']) {
$info = $_POST['info'];
header('location: last_page.php');
}[/HTML]
To send the '$info' variable to 'last_page.php' which will then do:
[HTML]echo $info;[/HTML]

The easiest option is to create a new form on 'processor.php'. But how do you activate a form without user input?

I hope I have explained myself. If not, please say so.
Thanks in advance,

pieter.

---

### Post by lnostdal on 2007-02-03
nah .. don't do that; you want sessions: [http://no.php.net/manual/en/ref.session.php](http://no.php.net/manual/en/ref.session.php)

---


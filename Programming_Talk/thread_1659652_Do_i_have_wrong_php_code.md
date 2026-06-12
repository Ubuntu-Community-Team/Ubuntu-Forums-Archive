---
title: "Do i have wrong php code?"
date: 2011-01-04
forum: Programming Talk
---

### Post by stamatiou on 2011-01-04
Hey guys, I have started learning php and I would like to make a simple calculator, so I tried to write one, sadly something is wrong and chrome doesn't open the file,
her is the code:
[PHP]<html>
<head><title></title></head>
<body>
<?php
if (!isset($_POST['submit'])&&(!isset($_POST['Submit'])){
?>
<form method = 'post' action = 'a.php' />
<input type = 'text' size "3" name = 'Num'/>
<input type = 'submit' name = 'submit' value = 'Submit'>
<input type = 'text' size "3" name = 'num'/>
<input type = 'submit' name = 'Submit' value = 'Submit'>
</form>
<?php
}
else {
	$num = $_POST['num']
	$Num = $_POST['Num']
	$plus = $num + $Num
	echo $plus
}
?>
</body>
</html>
[/PHP]
and here is a screenshot of what it shows me in the browser:
[http://www.mediafire.com/?1wocg87pjli5mzb]("http://www.mediafire.com/?1wocg87pjli5mzb")

---

### Post by Arndt on 2011-01-04
> **stamatiou said:**
> Hey guys, I have started learning php and I would like to make a simple calculator, so I tried to write one, sadly something is wrong and chrome doesn't open the file,
her is the code:
[PHP]<html>
<head><title></title></head>
<body>
<?php
if (!isset($_POST['submit'])&&(!isset($_POST['Submit'])){
?>
<form method = 'post' action = 'a.php' />
<input type = 'text' size "3" name = 'Num'/>
<input type = 'submit' name = 'submit' value = 'Submit'>
<input type = 'text' size "3" name = 'num'/>
<input type = 'submit' name = 'Submit' value = 'Submit'>
</form>
<?php
}
else {
	$num = $_POST['num']
	$Num = $_POST['Num']
	$plus = $num + $Num
	echo $plus
}
?>
</body>
</html>
[/PHP]
and here is a screenshot of what it shows me in the browser:
[http://www.mediafire.com/?1wocg87pjli5mzb]("http://www.mediafire.com/?1wocg87pjli5mzb")

Great Scott, what trashy site is that? Why does it shrink my browser window?

---

### Post by Wtower on 2011-01-04
Running on my netbook now so I can't really test, but from a first look I think that unlike eg c language, the html post arguments are case insensitive so I would change them from num and Num to something else.

---

### Post by stamatiou on 2011-01-04
> **Arndt said:**
> Great Scott, what trashy site is that? Why does it shrink my browser window?
Do you mean mediafire?

---

### Post by stamatiou on 2011-01-04
> **Wtower said:**
> Running on my netbook now so I can't really test, but from a first look I think that unlike eg c language, the html post arguments are case insensitive so I would change them from num and Num to something else.
Is this the mistake?

---

### Post by Wtower on 2011-01-05
I don't know, haven't you tried yet? :) I will be back to my office next week.

---


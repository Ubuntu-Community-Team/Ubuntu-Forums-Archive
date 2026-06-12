---
title: "problem with php explode..."
date: 2006-12-20
forum: Programming Talk
---

### Post by orlox on 2006-12-20
Hi....

I've been trying for a while to separate an string by it's double quotes (") using explode. When I try to do:

[PHP]
$splitString=explode('"',$stringBusqueda);
[/PHP]
or
[PHP]
$splitString=explode("\"",$stringBusqueda);
[/PHP]
or:
[PHP]
$splitString=explode('\"',$stringBusqueda);
[/PHP]
it doesn't work at all....it doesn't split the string into an array. But, if instead of double quotes, I try to use the symbol = it works, and splits the string when it has =:
[PHP]
$splitString=explode('=',$stringBusqueda);
[/PHP]
How can I split the string by its double quotes???

---

### Post by Paul41 on 2006-12-20
I just tried and this worked for me.

```
$splitString=explode('"',$stringBusqueda);
```

Could you have an error somewhere else?

---

### Post by orlox on 2006-12-20
Still not working :( ...

This is my code:

[PHP]
    $stringBusqueda=trim($stringBusqueda);
    $splitString=explode('"',$stringBusqueda);
    foreach($splitString as $rrr){
      echo $rrr.'<br/>';
    }
[/PHP]

If I give as input:

```
"in double quotes" not in "double quotes"
``` 

the result is simply:

```
"in double quotes" not in "double quotes"<br/>
```

I can't get it to perform the explode as I would expect ](*,)

---

### Post by Paul41 on 2006-12-20
Interesting, I just ran your code exactly and here is what I got.

> in double quotes
not in
double quotes

---

### Post by orlox on 2006-12-20
wonder what's the problem then....something with the character encoding, or maybe with the php configuration itself... it's truly strange :-k

---

### Post by Paul41 on 2006-12-20
Here is exactly what I used. 

```
$stringBusqueda = '"in double quotes" not in "double quotes"';
$stringBusqueda=trim($stringBusqueda);
$splitString=explode('"',$stringBusqueda);
foreach($splitString as $rrr){
	echo $rrr.'<br/>';
}
```

For everything except initially setting the $stringBusqueda variable I just copied your code. Could it be in the way that you are initially setting the variable?

---

### Post by orlox on 2006-12-20
I tested your code, and it works, so it seems you're right.

the value of the string is obtained through a posted form...but I still cat figure out how to solve it....

---

### Post by Paul41 on 2006-12-20
Here is a quick dummied up page that I did and it works. I had to use stripslashes to unescape the quotes, but I am not sure that this is your problem.

```
<?php
if (isset($_POST['txtTest'])) {
	#$stringBusqueda = '"in double quotes" not in "double quotes"';
	$stringBusqueda=$_POST['txtTest'];
	$stringBusqueda=stripslashes(trim($stringBusqueda));
	$splitString=explode('"',$stringBusqueda);
	foreach($splitString as $rrr){
		echo $rrr.'<br/>';
	} 
}
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
	   "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="en_US" xml:lang="en_US">
<head></head>
<body>
<form method="post" action="file.php">
<input type="text" name="txtTest" />
<input type="submit" />
</form>
</body>
</html>
```

---

### Post by orlox on 2006-12-20
well, there I made it work...I was using a framework, where the values from the post where accessed in a strabge way. I accessed it by simply using $_POST, and it worked right

THANX!!!

---


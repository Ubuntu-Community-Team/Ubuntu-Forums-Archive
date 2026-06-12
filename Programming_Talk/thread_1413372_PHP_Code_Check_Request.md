---
title: "PHP Code Check Request"
date: 2010-02-22
forum: Programming Talk
---

### Post by dhtseany on 2010-02-22
Hi guys,
Could someone tell me what's wrong with my code below? I'm mainly concerned about whether or not the variable $url has a value when the script loads. I should also add that currently, with the way it sits now, the variable $frame only returns the vaule "main.php". 

```

<?php
$url = $_GET['ft'];
$def = "main.php";
if ($url == 0) {
	$frame = $def;} 
else {
	$frame = $url;}
include('include/1.php');
include('include/misc.php');
echo $frame;
include('include/2.php');
?>

```

Specifically, the line:
```

if ($url == 0) {
	$frame = $def;} 

```
...is supposed to check if the variable $url is blank or not. Is this a good way to do this or is there a better way that I'm neglecting to use?

Thanks for looking!

Peace,
Sean

---

### Post by Hellkeepa on 2010-02-22
HELLo!

Don't have a lot of time now, so I'll just recommend you to read this post:
[http://ubuntuforums.org/showpost.php?p=8734772&postcount=8](http://ubuntuforums.org/showpost.php?p=8734772&postcount=8)

It's from a thread where someone wants to do almost exactly what you're doing, only with added use of the Apache Rewrite Engine (which you don't have to worry about). I've pointed out some good practises that should be followed, as well some common insecurities commited in both threads.

Happy codin'!

---


---
title: "PHP multiple forms submission"
date: 2011-05-06
forum: Programming Talk
---

### Post by hakermania on 2011-05-06
I've created this code in PHP and I'm a complete newbie (i've done something in the past regarding email-sending but nothing more...)
So, as I put this code inside my .php file and request it to load, an empty page is presented. What is the actual problem to the code?
Thx in advance for any answer!
```
<?php
$wfilename = $_POST["wfilename"];
$wbody = $_POST["wbody"];
$rfilename = $_POST["rfilename"];
?>
<html>
<head>
<title>Write/Read files!</title>
</head>
<body>
<h1>WRITE FILES</h1>
<form method="post" action="<?php echo $PHP_SELF;?>">
Write filename:<input type="text" size="30" maxlength="30" name="wfilename">:<br />
Body:<br /><textarea rows="20" cols="20" name="wbody" wrap="physical"></textarea><br /> 
<input type="submit" value="write" name="write"><br />
</form><br /> 

<br />
<h1>READ FILES</h1>
<form method="post" action="<?php echo $PHP_SELF;?>">
Write filename:<input type="text" size="30" maxlength="30" name="rfilename"><br />
<input type="submit" value="read" name="read"><br />
</form><br /> 


<?php
if ($_POST['read'])
{
$fh = fopen($rfilename, 'r') or die(":(");
$theData = fread($fh, 5);
fclose($fh);
echo "$rfilename contains:\n\n$theData";
}
else if ($_POST['write']) {
$fh = fopen($wfilename, 'w') or die("can't open file");
fwrite($fh, $wbody);
fclose($fh);
echo "$wbody was successfully written to $wfilename"
}

```

---

### Post by ChrisRatahi on 2011-05-06
Check to make sure all of your tags are closed (including body) by the looks of things that last php tag is not closed. This could cause your page to stop loading.

---

### Post by hakermania on 2011-05-07
This was a copy error actually :)
This isn't the problem

---


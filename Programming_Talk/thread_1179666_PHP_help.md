---
title: "PHP help"
date: 2009-06-05
forum: Programming Talk
---

### Post by KunoNoOni on 2009-06-05
I'm trying to convert a program that I wrote in Javascript over to PHP but I'm having some trouble. First here is the code:

```
<html>
<head>
<?
function generateCode(){
	$stringLen = strlen($thePassword);
	$xCode = 0;
	$asciiCode = 0;
	for ($i=0;$i < $stringLen;$i++){
		$eachChar = substr($thePassword,$i,1);
		if (is_nan($eachChar)){
			$asciiCode = ord($eachChar);
			$xCode += ($asciiCode * 1024)*64*128*1024/512;
		}
		else{
			$xCode += ($eachChar * 1024)*64*128*1024/512;
		}
	}
	round($xCode/=64);
	print $xCode;
	return false;
}

?>
<title></title>
</head>
<body>
Please enter in the password:
<form method="post" name="theForm" onSubmit="generateCode()">
<input type="text" name="thePassword" size="" value="">
</form>
</body>
</html>
```

The program is quite simple. The user enters in a password and that password is turned into a number. Now when I run the program and type in a password and hit return, nothing happens. I've even put in prints that say stuff like "test" or "is this thing working?" but they don't print out either...

So what am I doing wrong?

**Edit: Nevermind I figured out what I was doing wrong.**

KunoNoOni

---


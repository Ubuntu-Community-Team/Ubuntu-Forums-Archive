---
title: "Newbie in PHP, trying to write to file.."
date: 2011-01-22
forum: Programming Talk
---

### Post by hakermania on 2011-01-22
```
<html><head><title>Contact Form</title></head> 
<body bgcolor=FFFFFF> 
 
<center><p><center> 
<H1>Suggestions/Questions about Wallch Wallpaper Changer</h1> 
<table><tr><td> 
 
<? 
$text=$_POST["text"]; 
$email=strtolower($_POST["email"]); 
if (strpos($email,"@")==0 or strpos($email,".")==0){$email="";} 
if ($email!="" and $text!=""){ 
$message="$email\n\n$text"; 

if(mail('mail@gmail.com', 'My Subject', $message))
{
    echo "OK"
}
else
{
    echo "BAAAD";
} 
 
   print "<center>Thanks for your Suggestion/Question<p><a href=/>Home Page</a></center>"; 
}else{ 
?> 
 
<form action=<? print $_SERVER["PHP_SELF"]; ?> method=post> 
<p>Your contact email:<br> 
<INPUT NAME="email" SIZE="35" MAXLENGTH="65"> 
<BR>Your text:<br><TEXTAREA name=text cols=40 rows=5><? print $text; ?></TEXTAREA> 
<br><INPUT TYPE="SUBMIT" NAME=submit VALUE=Submit> 
</form> 
 
<? } ?> 
 
</td></tr></table> 
</center></body></html>
```What I want is simply to send an email... But I always get BAAD. I cannot check /var/log because I use a free host for this.

Can you help me :) ?

---


---
title: "Coding PHP for newbies. Why this page does not work?"
date: 2011-07-10
forum: Programming Talk
---

### Post by honeybear on 2011-07-10
Coding PHP for newbies. Why this page does not work?

test.php
```

<?


if ($_POST[submit]=="Submit")
{

$name=$_POST['name'];
checkOK($name);
$email=$_POST['email'];
checkOK($email);
$comments=$_POST['comments'];

echo ' <span style="font-weight: bold" > '  ;
echo ' ====>>>   Read/updated !   <<<==== ' ;
echo '</span> ' ;
echo '</div> ' ;
echo '<div style="text-align: left;"> '  ;

$message="$name just filled in your comments form. They said:\n$comments\n\nTheir e-mail address was: $email";
echo $message
}


?>


<form action="testi.php" method="post">
Your Name: <input type="text" name="name"><br>
E-mail: <input type="text" name = "email"><br><br>
Comments<br>
<textarea name="comments"></textarea><br><br>
<input type="submit" value="Submit">
</form>











```




Any inputs are welcome. I would like have all html and php working in this single upper test.php page.

Learning step-1

---

### Post by LoneWolfJack on 2011-07-10
you don't have a "checkOK" function.

---

### Post by unknownPoster on 2011-07-10
And my guess would be that you want something similar to this:
```
[FONT=Arial, Helvetica, sans-serif][SIZE=2][FONT=Arial][COLOR=#0000FF][COLOR=Black]function checkOK($field){
if (eregi("\r",$field) || eregi("\n",$field)){
die("Invalid Input!");
}
[/COLOR][/COLOR][/FONT][/SIZE][/FONT]
```[FONT=Arial, Helvetica, sans-serif][SIZE=2][FONT=Arial][COLOR=#0000FF][COLOR=Black]


[/COLOR][/COLOR][/FONT][/SIZE][/FONT]

---

### Post by v8YKxgHe on 2011-07-10
> **unknownPoster said:**
> And my guess would be that you want something similar to this:
```
function checkOK($field){
if (eregi("\r",$field) || eregi("\n",$field)){
die("Invalid Input!");
}
```

[http://php.net/ereg](http://php.net/ereg) has been deprecated for a long time and should not be used, please suggest [http://php.net/pcre](http://php.net/pcre) over it. Also, for such simple thing regex is not even needed. You can use [http://php.net/strpos](http://php.net/strpos) to check if a string contains a character. Only use regex when you need it.

honeybear, there are a few things that you're going to want to learn first, other wise you're going to fall into the trap of crap PHP code.

Firstly don't use short tags, the "<?". Instead use "<?php" - the reason for this is because short tags are not enabled on all servers, whereas "<?php" will work on every installation.

Next, ensure you have your "error_reporting" level high enough and that "display_errors" are on (for development). Right now you're going to be getting PHP notices regarding undefined constants. You can do this either in your php.ini configuration file (recommended) or add the following to the top of your script:

[php]error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', true);[/php]
You need to be quoting your array indexes, other wise PHP is going to try and find the constant called "submit" which does not exist. i.e. you need to do [PHP]$_POST['submit'][/PHP] **not**[PHP]$_POST[submit][/PHP]

Also, what do you mean your script does not work? We can't read minds.

---

### Post by unknownPoster on 2011-07-10
My mistake about ereg. I'll accept that.

However, I do advise using regular expressions as they are very powerful and tend to make for cleaner code in my experience.

One reason I don't like strpos for this kind of thing is the following taken from PHP docs:
> 
This function may return Boolean **FALSE**, but may also return a non-Boolean value which evaluates to **FALSE**, such as *0* or "". Please read the section on [Booleans]("http://www.php.net/manual/en/language.types.boolean.php") for more information. Use [the === operator]("http://www.php.net/manual/en/language.operators.comparison.php") for testing the return value of this function.

I prefer the preg_match() function for search for specific instances of characters.

---

### Post by v8YKxgHe on 2011-07-10
unknownPoster, that is no problem - just do as it says and use the === operator. The overhead of using regex for such simple operation is not a good idea.

To quote a famous saying:

> Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems.

Regex is good, just not when overused.

---


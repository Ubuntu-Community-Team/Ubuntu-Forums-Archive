---
title: "php and includes"
date: 2010-07-22
forum: Programming Talk
---

### Post by stormchaser on 2010-07-22
My goal is to have functions defined within include statements so that I can access my functions from anywhere on my site. If I do this:
```
function.php
<?php  ;
function helloworld() {
    echo "Hello World\n";
}

code.php
<?php
require_once "function.php";
helloworld();
?>
```
I get a wonderful "Call to undefined function error".

If I do this instead:
```
function.php
<?php  ;
class class1 {
    public static function helloworld() {
        echo "Hello World\n";
    }
}

code.php
<?php
require_once "function.php";
class1::helloworld();
?>
```

I get the output as desired.  Without the semicolon right after the <?php tag in either example, I get the "Call to Undefined Function" error.  I have no idea why the example using the class and the semicolon in the first line works when just defining the function in the first example doesn't (even with the semicolon).  Maybe I'm just missing something obvious here, but I'd really like to know why this behaves as it does?

---

### Post by ju2wheels on 2010-07-22
Unless you pasted it incorrectly, your first file should be:

```

<?php  
function helloworld() {
    echo "Hello World\n";
}

?>

```

Always remember to close the php tag at the end of the file.

Also when you include it, if these two files are not in the same folder, be sure to add the path to the file in the include (relative to your web root IIRC, havent used php in a while).

---

### Post by stormchaser on 2010-07-23
Hmmm...definitely a copy/paste error there.  That's what I get for staring at this for way too long...my apologies!

I think I've isolated the issue as I tried running this code on my localhost server instead of the remote server where it will be deployed, and this include worked just fine in all cases.  Is there some sort of apache directive or php ini setting that would keep include files from parsing correctly?

---

### Post by Bachstelze on 2010-07-23
> **ju2wheels said:**
> 
Always remember to close the php tag at the end of the file.


No. It is completely optional and, in fact, some projects forbid it in their coding style guidelines:

[http://framework.zend.com/manual/en/coding-standard.php-file-formatting.html#coding-standard.php-file-formatting.general](http://framework.zend.com/manual/en/coding-standard.php-file-formatting.html#coding-standard.php-file-formatting.general)

---

### Post by Hellkeepa on 2010-07-29
HELLo!

The fact of the matter is that the code posted in the OP, is entierly correct, so I suspect that there's something else going on. What is the exact error message you're getting, **stormchaser**?

Happy codin'!

---

### Post by grantoos on 2010-07-29
function.php
[PHP]
<?php  ; //Why is the semicolon there?
function helloworld() {
    echo "Hello World\n";
} //No ?> tag
[/PHP]code.php
[PHP]
<?php
require_once "function.php"; //should be in brackets: require_once("function.php");
helloworld();
?>
[/PHP]Try that and report back, because other than that it should work since it's just a simple function call.

---

### Post by stormchaser on 2010-07-31
Hi Guys.

Thanks for the suggestions.  I figured this one out, and it was unfortunately one of those glorious "Duh-oh" moments. :D  

The php file was included via an http address and not a local file path reference for some reason and that definitely doesn't work because it "returns" the http output instead of including the actual php code.

Guess I'll file that one away in the "never do that again for any reason" bin haha (and I don't know why I did it in the first place)

---


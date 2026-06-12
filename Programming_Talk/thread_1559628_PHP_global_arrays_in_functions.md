---
title: "PHP global arrays in functions"
date: 2010-08-23
forum: Programming Talk
---

### Post by vandorjw on 2010-08-23
Hey everyone,

I am fairly new to PHP, and I now have a problem that has been bugging me for a while.
Here is some example code to explain my problem.
[PHP]

<?php

$myArray array('first','second','third');

function myFunct1(){
   global $myArray;
   if(//stuff){
      $myArray = array("first" => "Errors Occurred, Please Try Again.");
   }
}

function myFunct2(){
   global $myArray;
   if(//stuff){
      $myArray = array("second" => "Errors Occurred, Please Try Again.");
   }
}

function myFunct3(){
   global $myArray;
   if(//stuff){
      $myArray = array("third" => "Errors Occurred, Please Try Again.");
   }
}

myFunct1();
myFunct2();
myFunct3();
print_r($myArray);

?>
[/PHP]

What I expect to happen, is that if the IF statement is true in each case, the array should hold 3 different strings. However what it does is, only ever keep the last string written to it. Can someone explain to me why it would do this?

If it doesn't make sense, I have attached my actual code with some examples.

Thanks - CC7

## SOLVED ##

I realized that
[PHP]$myArray = array("third" => "Errors Occurred, Please Try Again.");[/PHP]
AND
[PHP]$myArray["third"] = "Errors Occurred, Please Try Again.";[/PHP]
are NOT the same. The fist one (re)-creates an array. The second one updates the index!

---

### Post by Reiger on 2010-08-23
You will want to read up on the global keyword. It tells PHP that a variable should be acessed from global scope rather than from local (function) scope.

---

### Post by Hellkeepa on 2010-08-27
HELLo!

I don't recommend using the global keyword, for many reasons. What I'd do, in this case, is probably something like this:
[php]<?php
function My_Func_1 () {
    if (true) {
        return "Message 1";
    }
}

function My_Func_2 () {
    if (true) {
        return "Message 2";
    }
}
function My_Func_3 () {
    if (true) {
        return "Message 3";
    }
}

$Messages = array ();
$Messages['first'] = My_Func_1 ();
$Messages['second'] = My_Func_2 ();
$Messages['third'] = My_Func_3 ();
[/php]
Though, this is a very constructed example, and if the app looks like this in real life I would probably have reconsidered some of my design calls.

Happy codin'!

---

### Post by vandorjw on 2010-08-27
Hey thanks for the help with what I thought to be a solved problem. :)

@Reiger - Yep I know. Without the global keyword, my functions would just create another local array, and destroy that array when the functions are done. With the Global, they use the "Global" Array instead.

@ Hellkeepa - What is wrong or..why should I not use a global? It works fine. Could you give me a link that describes some of the drawbacks?

Thanks - CC7

---

### Post by Xeoncross on 2010-08-27
I would do it a little more like this:

[PHP]

class Messages
{
	public static $messages = array();
	
	public static function set($key, $message)
	{
		self::$messages[$key] = $message;
	}
}

function myFunct1()
{
	if(TRUE)
	{
		Messages::set("first", "Errors Occurred, Please Try Again.");
	}
}

function myFunct2()
{
	if(TRUE)
	{
		Messages::set("second", "Errors Occurred, Please Try Again.");
	}
}

print_r(Messages::$messages);
?>[/PHP]

---

### Post by Hellkeepa on 2010-09-01
HELLo!

**cc7gir**: Mainly it's a readability issue, as it makes tracking what happens to the global variable *that* much harder. Especially in larger codebases. This, in turn, introduces a huge risk for more bugs. Bugs which can be quite troublesome to debug.
It also may introduce a security risk, or rather amplify a security risk.

Here's a couple of articles on the issue, and you can find more with a simple google search:
[http://www.webapper.com/blog/index.php/2008/01/22/a-new-reason-to-not-use-global-variables/](http://www.webapper.com/blog/index.php/2008/01/22/a-new-reason-to-not-use-global-variables/)
[http://c2.com/cgi/wiki?GlobalVariablesAreBad](http://c2.com/cgi/wiki?GlobalVariablesAreBad)
[http://en.wikipedia.org/wiki/Global_variable](http://en.wikipedia.org/wiki/Global_variable)

**Xeoncross**: While I might be inclined to agree that a OOP-implementation would perhaps be better in most cases you'd see something like this, I don't think it's the best option to spring upon somone who's as new as the OP seems to be.

Happy codin'!

---


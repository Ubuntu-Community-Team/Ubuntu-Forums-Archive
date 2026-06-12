---
title: "Displaying multiple if statement output messages in PHP"
date: 2010-02-27
forum: Programming Talk
---

### Post by blueshiftoverwatch on 2010-02-27
If I were making a forum with textboxes that the user had to enter data into and wanted multiple error messages to show up if the user either didn't enter in the right type of information (e.g. letters in a number only field, vice versa, skipping a required field) how would I go about that?

Currently I'm using an if statement with the die command. But, that only displays one error message at a time.

For example, with this type of code if the user didn't type in anything the only error message he would get would be "Enter your name". Not, that plus the other two fields.
[php]if($FullName == null) {
die("Enter your name");
}
        
if($PhoneNumber == null) {
die("Enter your number");
}

if(is_numeric($PhoneNumber) == false) {
die("Must only use numeric characters in the 'phone number' field");
}[/php]
1. How would I tell PHP to perform all of the above tests before spitting out any output and once that was done? I'm assuming that since there exists order of operations code for math problems that will tell it to do X part of the equation before doing Y part that there is also some way to tell it to calculate certain if statements (or in this case, a batch of if statements) before moving on.

2. What function(s) exist that would tell PHP to keep going instead of stopping after the first if statement wasn't satisfied. The die function isn't satisfactory because it stops the entire process after the first if statement isn't satisfied. In this instance, the die function could only be used on the last if statement in the batch.

3. How could I tell PHP to print/echo out the error messages in different locations? Is there some way I could attach a print function to each specific if statement. So I could choose where the error message was printed to. For example, if I had input/outputs assigned to a table and wanted each error message to print to a specific row/column on the XY plain.

---

### Post by ja660k on 2010-02-27
> **blueshiftoverwatch said:**
> If I were making a forum with textboxes 
1. How would I tell PHP to perform all of the above tests before spitting out any output and once that was done? I'm assuming that since there exists order of operations code for math problems that will tell it to do X part of the equation before doing Y part that there is also some way to tell it to calculate certain if statements (or in this case, a batch of if statements) before moving on.

2. What function(s) exist that would tell PHP to keep going instead of stopping after the first if statement wasn't satisfied. The die function isn't satisfactory because it stops the entire process after the first if statement isn't satisfied. In this instance, the die function could only be used on the last if statement in the batch.


you want something like
[PHP]
$error = 0;

if($FullName == null) {
    echo "Enter your name";
    $error ++;
}
        
if($PhoneNumber == null) {
    echo "Enter your number";
    $error ++;
}

if(is_numeric($PhoneNumber) == false) {
    echo "Must only use numeric characters in the 'phone number' field";
    $error ++;
}  
if($error != 0){
   die();
}

[/PHP]
or something like that.

> **blueshiftoverwatch said:**
> 
3. How could I tell PHP to print/echo out the error messages in different locations? Is there some way I could attach a print function to each specific if statement. So I could choose where the error message was printed to. For example, if I had input/outputs assigned to a table and wanted each error message to print to a specific row/column on the XY plain.

use some javascript, im not sure on the syntax because im not on my laptop.
BUT have a div with the error msg in it, hide it. then in the php instead of echo the error
echo the javascript to change that giv to visible

if that makes sense?

---

### Post by Hellkeepa on 2010-02-28
HELLo!

First off I think we need to cover some basics, as you don't seem to be too familiar with how PHP works.

Since PHP is executed on the server, before anything is sent to the browser*, you gain complete control to create whatever structure in the HTML code you like. Including a complete replacement of the resulting content that is sent to the browser, depending upon the execution tree which the code follows. PHP will also execute the code in its entirety, unless otherwise specified. Either via control structures like IF, or via forced aborts with "return" or "die()"
So the question isn't "is there a way to tell PHP to keep going", that is what it normally does. What you did, was to tell it to stop. Not telling it to stop, is what you wanted to do. ;-)

Secondly, since PHP is used to construct the HTML code and content of a web page, and it is a procedural language, everything you do in it should follow a set order. The same order you'd like to use for the logic of the script, which is how you control where things are printed within the context of the finished HTML code.
If you want to spread the error messages around in the HTML code, then you need to store each message into its own variable. Then print those variables out, at their correct place in the HTML code. If you're using a templating system, which does not have to be advanced at all, this will make this a lot easier to understand and read. It'll also help you keep the HTML and PHP code separate, which is a great help both in writing the code and in reading it later on. Mixed mode (mixing PHP and HTML) also severely limits the options you have available, which makes certain tasks impossible, when they should have been trivial.

Here's a good example of how I'd do it: [http://norskwebforum.no/pastebin/10144](http://norskwebforum.no/pastebin/10144)
This particular code is taken from a contact form, and is included from the main script. Thus the "return" in the middle there, to stop parsing the contact form code, and return to the main script. The "Validate ()" function is just a wrapper function for my validation functions, so that I can take advantage of my template engine to generate a localized error message.

** Actually, this is not entirely correct in all cases, but true enough for the point in my post. *

*Edit, added:*: Hehe, sorry, **iMisspell**. :-P Nice to see we're thinking more or less in the same manner. :-)

Happy codin'!

---

### Post by iMisspell on 2010-02-28
Or use javascript for the whole thing.
When the form is submitted, have a javascript to a check and pop a alert() to the user.

Nice thing about that, its instant since its all done client side.
Bad thing about that, browser compatability, javascript can be a pain for cross browser.

Just an idea.

You could also do something like...
Which will print out multipule errors.
[PHP]

$error = null;

if($FullName == null) {
    $error .= "Enter your name <br />";
}
     
if($PhoneNumber == null) {
    $error .= "Enter your number <br />";
}

if(!is_numeric($PhoneNumber) && $PhoneNumber != null) {
    $error .= "Must only use numeric characters in the 'phone number' field <br />";
} 

if($error){
   die($error);
}  

[/PHP]

Or...
Create the submit-form from a template, leave a div tag or table cell empty (where you wish to display an error if it happens), do a check with PHP when its submitted, if error, load submit-form again and print the error.

This will be very rough, sorry, but im tired...
[PHP]
// template...
function displayForm($info = '', $error = ''){
$out = '<form>
   <input name="FullName" value="'. $info['FullName'] .'"/> Name <div id="error">'. $error['FullName'] .'</div>
   <input name="PhoneNumber" value="'. $info['PhoneNumber']. '"/> Phone <div id="error">'. $error['PhoneNumber'] .'</div>
</form>';

return $out;


}


// submit check...
$error = false;
$errMsg = null;

if($FullName == null) {
    $errMsg['FullName'] = "Enter your name";
    $error = true;
}
     
if($PhoneNumber == null) {
    $errMsg['PhoneNumber'] = "Enter your number";
    $error = true;
}


if(!is_numeric($PhoneNumber) && $PhoneNumber != null) {
    $errMsg['PhoneNumber'] = "Must only use numeric characters in the 'phone number' field";
    $error = true;
} 

 
if($error != 0){
   print(displayForm($_POST, $errMsg));
   die();
}
[/PHP]

something like that...


[edit]
Dam.., Hellkeepa
If you only posted that 2 more minutes earlyer, i could have save my energy :D

_

_

---

### Post by Simon17 on 2010-02-28
Question: Why call die()?

Wouldn't you want to display the form again to let the user fix it?

---


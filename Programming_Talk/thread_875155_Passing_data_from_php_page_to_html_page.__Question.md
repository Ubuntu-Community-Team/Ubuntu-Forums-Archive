---
title: "Passing data from php page to html page.  Question from a beginner."
date: 2008-07-30
forum: Programming Talk
---

### Post by tc101 on 2008-07-30
I am just learning php. 

I have crated 2 web pages.  Page test01.html accepts data in a form and then passes it to page test02.php using this statement: 

<form action="test02.php" method="post"

Page test02.php uses the data passed from test01.html to update a database.  I have all of this working.

I am confused about reading data from the database in test02 and passing it back to be displayed in test01.  Can that be done?

All the examples I have seen show a page like test02 creating a web page on the fly using data from the database, putting it all in in a big string like $display_block and then using: 

echo $display_block; 

Is this the only way to do it?

What if test01.html is a big elaborate web page and all you want to do is display one extra name in it.  You get that name  from the database you read in test02.php.  Do you have to rebuild all of test01.html with code in test02.php, or is there some way you can just pass back that one name?

---

### Post by LaRoza on 2008-07-30
You just query the database to get the data. I don't see what the problem is.

---

### Post by tc101 on 2008-07-30
I understand that I query the database to get the data.  I don't understand how to put that data from the server side php into the client side html. 

This may show a very basic lack of understanding on my part.  Remember I am a beginner.  Could someone point me at some sample code?

---

### Post by LaRoza on 2008-07-30
> **tc101 said:**
> I understand that I query the database to get the data.  I don't understand how to put that data from the server side php into the client side html. 

This may show a very basic lack of understanding on my part.  Remember I am a beginner.  Could someone point me at some sample code?

[php]
$results = query_database();

echo "The results are".$results;

[/php]

You just echo it. Remember, all the php is executed before the document is sent. (query_database() is just a function to hold the place of actually connecting and querying)

---

### Post by tc101 on 2008-07-30
Thanks LaRoza.  I see it clearly now.  I was confused learning several things at once.

---

### Post by mssever on 2008-07-31
> **LaRoza said:**
> Remember, all the php is executed before the document is sent.
That's not necessarily true. If you're using output buffering it's true, but otherwise, any echoed data gets sent as soon as it's flushed (implicitly or explicitly), even if the script hasn't finished yet.

---

### Post by henchman on 2008-07-31
buffered data will also be sent when the buffer is being flushed :tongue:

---

### Post by Reiger on 2008-07-31
But if you're not into complex OO-style PHP apps yet; your output will always be 'in order', regardless. (Because you'll be computing the first thing you want to output before you begin your second computation.)

And of course if things should turn nasty, you can always avoid the problem by 'queueing' the output in order, in a 'dump' string. It's not the preferred way; but it will work.

---

### Post by henchman on 2008-08-01
I would avoid using a "dump" string, but using these functions described here 

[http://www.php.net/manual/en/ref.outcontrol.php](http://www.php.net/manual/en/ref.outcontrol.php)

there are good examples on the pages which describe the specific functions, i would start reading about ob_start :)

---

### Post by cszikszoy on 2008-08-01
> **tc101 said:**
> What if test01.html is a big elaborate web page and all you want to do is display one extra name in it.  You get that name  from the database you read in test02.php.  Do you have to rebuild all of test01.html with code in test02.php, or is there some way you can just pass back that one name?

With PHP you can also embed any php code into an html page.  What you should try, is take test01.html, and rename it to testo1.php.

Then, somewhere on the page put this code:
```
<?php echo "hello"; ?>
```When writing html data with php, it's not necessary to put echo "<html> <head> ..." etc etc all over the place.

If you just close the php tags the web server should intrepret everything else as html by default.

Also, if your server setup supports it you can use the abbreviated php tags of <?  ?>.

Once you understand this, you can create a sort of php file that contains all of your function definitions, and leave it on the server to do all of the work.  Maybe in this function file you can include the function EchoResults();

Somewhere near the top of your html file, include this code:
```
<? include "functions.php"; ?>
or
<? require "functions.php"; ?>
```
require is usually the preferred way, because it will prevent the rest of the page from executing if it can't find functions.php on the server.  However, include will still work.

Then, in the html file, just include this code:
```
<? echo EchoResults(); ?>
```

---

